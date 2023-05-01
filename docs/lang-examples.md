# AgentLang example programs
This document demonstrates example programs in the **AgentLang** programming language.

## Epidemic
This program simulates the epidemic using people as agents.
```
DEFINE WIDTH = 500;
DEFINE HEIGHT = 500;

AGENT person {
    VARIABLE x: RANDOM(0, WIDTH) = x + RANDOM(0, 1) - 0.5;
    VARIABLE y: RANDOM(0, HEIGHT) = y + RANDOM(0, 1) - 0.5;

    CONST inf_probability = 0.1;
    CONST inf_distance = 3;
    CONST inf_timespan = 14;

    DYNAMIC days_remaining = IF infected THEN days_remaining - 1 ELSE inf_timespan;

    DYNAMIC neighbours = FILTER(AGENTS(person) AS p, SQRT(x * p.x + y * p.y) < inf_distance);
    DYNAMIC infected_neighbours = FILTER(neighbours AS p, p.infected == TRUE);
    DYNAMIC should_infect = RANDOM(0, 1) < inf_probability;
    
    DYNAMIC infected = (infected AND days_remaining > 0) OR (COUNT(in_proximity) > 0 AND should_infect);
}

GENERATE(person, 100);
```

## Flocking
This program simulates bird flocking using two types of agents.
```
DEFINE WIDTH = 500;
DEFINE HEIGHT = 500;

AGENT bird_leader {
    VARIABLE turn_angle: RANDOM(0, 360) = turn_angle + turn_magnitude * RANDOM(-1, 1);

    VARIABLE x: RANDOM(0, WIDTH) = x + speed * COS(turn_angle);
    VARIABLE y: RANDOM(0, HEIGHT) = y + speed * SIN(turn_angle);

    CONST speed = 3;
    CONST turn_magnitude = 3;
}

AGENT bird_follower {
    VARIABLE x: RANDOM(0, WIDTH) = x + speed * COS(turn_angle);
    VARIABLE y: RANDOM(0, HEIGHT) = y + speed * SIN(turn_angle);

    CONST speed = 3;

    DYNAMIC closest = MIN(AGENTS(bird_leader) AS bl, SQRT(x * bl.x + y * bl.y))
    DYNAMIC turn_angle = ARCTAN(closest.y - y, closest.x - x) * 0.5;
}

GENERATE(bird_leader, 10);
GENERATE(bird_follower, 20);
```