<img src="./assets/logos/agent-lang-logo-black.png#gh-light-mode-only" width="220">
<img src="./assets/logos/agent-lang-logo-white.png#gh-dark-mode-only" width="220">

![Version Badge](https://img.shields.io/badge/version-1.0.0-blue?style=flat)
![Contributors Badge](https://img.shields.io/badge/contributors-1-green?style=flat)
![License Badge](https://img.shields.io/badge/license-MIT-red?style=flat)

## About
AgentLang is an interpreted programming language designed for agent-based modeling. Below is an example AgentLang source code.
```
agent snowflake 200 {

    const speed = random(8, 15);

    property x: random(0, width()) = x;
    property y: random(0, height()) = (y + speed) % height();
    
    const w = 10;
    const h = 10;
}
```

## Interpreter
For further details about the AgentLang interpreter, visit the [agent-lang-interpreter](https://github.com/TomasBoda/agent-lang-interpreter) repository.

## Web Interface
For further details about the AgentLang web interface, visit the [agent-lang-web](https://github.com/TomasBoda/agent-lang-web) repository.

## Live Demo
To try out AgentLang, visit the [AgentLang website](https://agent-lang-web.vercel.app) for live code sandbox and simulation modeling.

## Documentation
Documentation to the AgentLang programming language can be found on the [documentation page](https://agent-lang-web.vercel.app/documentation) of the AgentLang website.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](/LICENSE.md)

Made by [Tomas Boda](https://github.com/TomasBoda)
