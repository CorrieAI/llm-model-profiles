# LLM Model Profiles

A centralized repository of model profiles for various Large Language Models (LLMs). These profiles contain configuration settings, capabilities, and metadata for different AI models from various providers.

## Overview

This repository serves as a single source of truth for LLM model configurations, used by multiple projects including:
- [Fairyloft](https://github.com/yourusername/fairyloft) - AI story generation for children
- [Fairyloft Prompt Generator](https://github.com/yourusername/fairyloft-prompt-generator) - Prompt optimization across different LLMs

## Structure

```
profiles/
├── openai/
│   ├── gpt-4-1.yaml
│   ├── gpt-4o.yaml
│   ├── gpt-4o-mini.yaml
│   └── ...
├── anthropic/
│   ├── claude-3-5-sonnet.yaml
│   └── ...
├── local/
│   ├── llama-3.2-8b-local.yaml
│   └── ...
└── ...
```

## Profile Schema

Each model profile contains:

```yaml
name: Human-readable model name
provider: Provider name (openai, anthropic, local, etc.)
model: Model identifier used in API calls
api_base: API endpoint URL
api_key_env_var: Environment variable name for API key
temperature: Default temperature setting
max_tokens: Maximum tokens for generation
context_window: Model's context window size
description: Brief description of the model
supports_images: Whether the model supports image inputs
supports_tools: Whether the model supports function calling
provider_settings: Provider-specific settings
recommended_for: Use case recommendations
cost_estimate: Pricing information
```

## Usage

### As a Git Submodule

Add this repository as a submodule to your project:

```bash
git submodule add https://github.com/yourusername/llm-model-profiles.git model_profiles
git submodule init
git submodule update
```

### Direct Usage

Clone and use the profiles directly:

```python
import yaml
from pathlib import Path

def load_model_profile(provider: str, model_name: str):
    profile_path = Path(f"profiles/{provider}/{model_name}.yaml")
    with open(profile_path) as f:
        return yaml.safe_load(f)

# Example
gpt4_profile = load_model_profile("openai", "gpt-4-1")
```

## Contributing

1. Follow the existing schema when adding new profiles
2. Test the profile with actual API calls
3. Include accurate context window and token limits
4. Document any provider-specific settings
5. Submit a pull request with your changes

## Profile Guidelines

- **Accuracy**: Ensure all limits and capabilities are accurate
- **Completeness**: Include all required fields
- **Updates**: Keep profiles updated as models evolve
- **Documentation**: Add comments for non-obvious settings

## License

MIT License - See LICENSE file for details