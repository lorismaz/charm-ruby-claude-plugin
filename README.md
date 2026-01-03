# Charm Ruby Plugin for Claude Code

Build beautiful, interactive command-line applications in Ruby using the [charm-ruby](https://charm-ruby.dev) ecosystem.

## What is Charm Ruby?

Charm Ruby is a collection of Ruby gems ported from [Charm.sh](https://charm.sh)'s Go libraries by Marco Roth. It provides everything you need to build stunning terminal user interfaces:

| Gem | Purpose |
|-----|---------|
| **bubbletea** | Model-View-Update architecture for interactive apps |
| **lipgloss** | CSS-like terminal styling |
| **bubbles** | Pre-built components (spinners, inputs, lists, tables) |
| **huh** | Interactive forms with validation |
| **glamour** | Markdown rendering in terminal |
| **harmonica** | Physics-based spring animations |
| **gum** | Shell script interactions |
| **bubblezone** | Mouse event tracking and clickable zones |
| **ntcharts** | Terminal charts (sparklines, bar/line charts, heatmaps) |

## Features

### Skill: Charm Ruby Development

Comprehensive knowledge for building CLI tools:

- Quick start guides
- Bubble Tea MVU architecture patterns
- Lipgloss styling reference
- Component integration
- Best practices
- Gem distribution

Triggered when you ask about building CLI tools in Ruby, terminal UIs, or any charm-ruby library.

### Commands

| Command | Description |
|---------|-------------|
| `/charm:init [name]` | Scaffold a new charm-ruby CLI project |
| `/charm:add-component [type]` | Add a Bubbles component to your project |
| `/charm:package` | Prepare your CLI for RubyGems distribution |

### Agent: CLI Architect

Expert Ruby CLI architect that helps you:

- Design application architecture
- Plan multi-screen navigation
- Select appropriate components
- Structure your Bubble Tea models
- Follow terminal UX best practices

## Quick Start

1. **Create a new project:**
   ```
   /charm:init my-awesome-cli
   ```

2. **Add components as needed:**
   ```
   /charm:add-component list
   /charm:add-component spinner
   ```

3. **When ready to publish:**
   ```
   /charm:package
   ```

## Example: Simple Counter

```ruby
require "bubbletea"
require "lipgloss"

class CounterModel
  include Bubbletea::Model

  def initialize
    @count = 0
    @style = Lipgloss::Style.new.bold(true).foreground("#FF69B4")
  end

  def init
    nil
  end

  def update(msg)
    case msg
    when Bubbletea::KeyMsg
      case msg.string
      when "q" then return [self, Bubbletea.quit]
      when "up", "k" then @count += 1
      when "down", "j" then @count -= 1
      end
    end
    [self, nil]
  end

  def view
    "Count: #{@style.render(@count.to_s)}\n\n↑/k inc • ↓/j dec • q quit"
  end
end

Bubbletea.run(CounterModel.new)
```

## Resources

- [charm-ruby.dev](https://charm-ruby.dev) - Official documentation
- [Marco Roth's blog post](https://marcoroth.dev/posts/glamorous-christmas) - Comprehensive overview
- [charm.sh](https://charm.sh) - Original Go libraries

## Installation

1. Add the marketplace:
   ```bash
   claude plugins marketplace add lorismaz/charm-ruby-claude-plugin
   ```

2. Install the plugin:
   ```bash
   claude plugins add charm-ruby@charm-ruby
   ```

The skill, commands, and agent will be automatically available after installation.

## License

MIT
