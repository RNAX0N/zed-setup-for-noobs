# zed-setup-for-noobs
A simple guide on setting up Zed editor for people switching from VSCode or generally inexperienced users

Initial Configuration:

Zed can be configured through the GUI, but the best way to do it (and the way the changes are actually applied) is through the settings.json file.

On Linux (most distros), this file is at ~/.config/zed/settings.json
(~/ refers to /home/{user}/ for Linux newbies. So /home/{yourusername}/.config/zed/settings.json)

Example: (Also @ settings.json in this repository)
The following example disables telemetry, disables vim mode to give similar keymapping to VSCode, and includes an Ollama qwen2.5-coder:32b local model as well as Gemini 3 for AI assistance.
Examples are given for setting fonts, font sizes, cursor behavior, and overall theming while applying the project panel on the left, similar to VSCode.
Newbies: // the start of a line signals a comment that does not get parsed
json "keys" are signaled within blocks of {}

'''jsonc
{
  // AI assistant configuration
  "agent": {
    // Active AI personality to use on startup
    "default_profile": "write",
    "profiles": {
      // User-defined profile named "Custom"
      "custom": {
        "default_model": {
          "provider": "zed.dev",
          "model": "gemini-3-pro-preview" // Uses Gemini via Zed API
        },
        "name": "Custom",
        "tools": {},
        "enable_all_context_servers": false, // Restricts access to external context
        "context_servers": {}
      }
    },
    // Global fallback model (Local Ollama instance)
    "default_model": {
      "provider": "ollama",
      "model": "qwen2.5-coder:32b"
    },
    "model_parameters": []
  },
  // Privacy: Disable data reporting to Zed
  "telemetry": {
    "diagnostics": false,
    "metrics": false
  },
  "ui_font_size": 12, // Interface text size
  "buffer_font_size": 10, // Code editor text size
  // Appearance settings
  "theme": {
    "mode": "system", // Syncs with OS light/dark mode
    "light": "One Light",
    "dark": "One Dark"
  },
  "vim_mode": false, // Vim keybindings disabled
  "autosave": "on_focus_change", // Saves when window loses focus
  // Integrated terminal styling
  "terminal": {
    "font_family": "Fira Code",
    "font_size": 10,
    "blinking_cursor": false
  },
  "tabs": {
    "git_status": true // Color tabs based on Git state (modified/added)
  },
  // File explorer sidebar
  "project_panel": {
    "dock": "left",
    "file_icons": true
  }
}
'''

Full Configuration Options List available at: https://www.kevnu.com/en/posts/zed-editor-configuration-guide-autosave-prettier-terminal-font-and-formatting-made-easy
