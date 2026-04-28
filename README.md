# Auto-plan Plugin for Home Assistant

A plugin for [local-ai-home-assistant](https://github.com/doctarock/local-ai-home-assistant/) that provides decision automation for worker agents. This plugin injects six core decision principles into worker task prompts to help auto-resolve common intermediate questions during task execution.

## Features

The plugin implements the six core decision principles from gstack's(https://github.com/garrytan/gstack) autoplan decision engine:

1. **Choose Completeness** - Always prefer complete solutions over shortcuts
2. **Fix the Full Blast Radius** - Address the entire class of problem, not just the instance
3. **Choose the Cleaner Path** - Prefer simpler, less complex solutions
4. **Don't Repeat Yourself** - Reuse existing patterns before creating new ones
5. **Explicit Over Clever** - Write obviously correct code over impressively terse code
6. **Bias Toward Action** - Proceed when you have enough information rather than seeking unnecessary clarification

## Installation

1. Clone this repository into your Home Assistant plugins directory
2. Ensure the plugin file is located at `autoplan/autoplan-plugin.js`
3. Restart your Home Assistant instance
4. The plugin will automatically register its tools and hooks

## Usage

The plugin provides three main tools for worker agents:

### autoplan_resolve
Resolve a specific intermediate decision using autoplan principles.

**Parameters:**
- `decision` (string, required): The decision you are facing
- `context` (string, optional): Additional context about the situation

### autoplan_principles
Get the full text of all six autoplan decision principles.

**Parameters:**
- `abridged` (boolean, optional): Return a short summary instead of full principles (default: false)

### autoplan_checklist
Run through the autoplan preflight checklist before starting a task.

**Parameters:**
- `taskDescription` (string, required): What you are about to do

## How It Works

The plugin automatically injects abridged decision principles into:
- Worker system prompts (for better intermediate decisions)
- Intake system prompts (for better routing/clarification decisions)
- Intake tool lists (so intake agents can access autoplan tools)

This ensures that all agents in the system make decisions aligned with the autoplan principles without needing explicit tool calls for every decision.

## Security

This plugin runs in-process with no external network access, file system access, or execution capabilities. It only provides decision-making guidance through prompt injection and tool responses.

## License

See LICENSE file for details.

## Author

OpenClaw Observer