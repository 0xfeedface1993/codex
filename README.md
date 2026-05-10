<p align="center"><code>npm i -g @openai/codex</code><br />or <code>brew install --cask codex</code></p>
<p align="center"><strong>Codex CLI</strong> is a coding agent from OpenAI that runs locally on your computer.
<p align="center">
  <img src="https://github.com/openai/codex/blob/main/.github/codex-cli-splash.png" alt="Codex CLI splash" width="80%" />
</p>
</br>
If you want Codex in your code editor (VS Code, Cursor, Windsurf), <a href="https://developers.openai.com/codex/ide">install in your IDE.</a>
</br>If you want the desktop app experience, run <code>codex app</code> or visit <a href="https://chatgpt.com/codex?app-landing-page=true">the Codex App page</a>.
</br>If you are looking for the <em>cloud-based agent</em> from OpenAI, <strong>Codex Web</strong>, go to <a href="https://chatgpt.com/codex">chatgpt.com/codex</a>.</p>

---

## Quickstart

### Installing and running Codex CLI

Install globally with your preferred package manager:

```shell
# Install using npm
npm install -g @openai/codex
```

```shell
# Install using Homebrew
brew install --cask codex
```

Then simply run `codex` to get started.

<details>
<summary>You can also go to the <a href="https://github.com/openai/codex/releases/latest">latest GitHub Release</a> and download the appropriate binary for your platform.</summary>

Each GitHub Release contains many executables, but in practice, you likely want one of these:

- macOS
  - Apple Silicon/arm64: `codex-aarch64-apple-darwin.tar.gz`
  - x86_64 (older Mac hardware): `codex-x86_64-apple-darwin.tar.gz`
- Linux
  - x86_64: `codex-x86_64-unknown-linux-musl.tar.gz`
  - arm64: `codex-aarch64-unknown-linux-musl.tar.gz`

Each archive contains a single entry with the platform baked into the name (e.g., `codex-x86_64-unknown-linux-musl`), so you likely want to rename it to `codex` after extracting it.

</details>

### Using Codex with your ChatGPT plan

Run `codex` and select **Sign in with ChatGPT**. We recommend signing into your ChatGPT account to use Codex as part of your Plus, Pro, Business, Edu, or Enterprise plan. [Learn more about what's included in your ChatGPT plan](https://help.openai.com/en/articles/11369540-codex-in-chatgpt).

You can also use Codex with an API key, but this requires [additional setup](https://developers.openai.com/codex/auth#sign-in-with-an-api-key).

### Using a custom model provider

To run this build without OpenAI account login, configure a custom
OpenAI-compatible provider in `~/.codex/config.toml`.

```toml
# The provider id must match the table name below.
model_provider = "custom"

# Use the model id exposed by your provider.
model = "your-model-id"

# Avoid the built-in release update check.
check_for_update_on_startup = false

[analytics]
enabled = false

[features]
# Disable ChatGPT/Codex Apps connectors and plugin discovery surfaces.
apps = false
tool_suggest = false
plugins = false

[model_providers.custom]
name = "Custom OpenAI-Compatible Provider"
base_url = "https://your-provider.example.com/v1"
env_key = "CUSTOM_PROVIDER_API_KEY"
wire_api = "responses"
requires_openai_auth = false

# Optional but recommended defaults.
request_max_retries = 4
stream_max_retries = 5
stream_idle_timeout_ms = 300000
websocket_connect_timeout_ms = 15000
supports_websockets = false
```

Then set the provider API key before starting Codex:

```shell
export CUSTOM_PROVIDER_API_KEY="your-api-key"
codex
```

`env_key` is sent as `Authorization: Bearer <value>`. If you previously signed
in with ChatGPT and want to avoid all OpenAI official cloud and connector
features, run `codex logout` before using the custom provider.

## Docs

- [**Codex Documentation**](https://developers.openai.com/codex)
- [**Contributing**](./docs/contributing.md)
- [**Installing & building**](./docs/install.md)
- [**Open source fund**](./docs/open-source-fund.md)

This repository is licensed under the [Apache-2.0 License](LICENSE).
