{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "console_title_template": "{{ .Shell }} in {{ .Folder }}",
  "blocks": [
    {
      "type": "prompt",
      "alignment": "left",
      "segments": [
        {
          "properties": {
            "cache_duration": "none"
          },
          "leading_diamond": "\ue0b6",
          "template": " {{ .UserName }} ",
          "foreground": "#ffffff",
          "background": "#c386f1",
          "type": "session",
          "style": "diamond"
        },
        {
          "properties": {
            "cache_duration": "none",
            "folder_separator_icon": " \ue0b1 ",
            "home_icon": "\ueb06",
            "style": "folder"
          },
          "template": " \uea83  {{ .Path }} ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "background": "#ff479c",
          "type": "path",
          "style": "powerline"
        },
        {
          "properties": {
            "branch_max_length": 25,
            "cache_duration": "none",
            "fetch_stash_count": true,
            "fetch_status": true,
            "fetch_upstream_icon": true
          },
          "leading_diamond": "\ue0b6",
          "trailing_diamond": "\ue0b4",
          "template": " {{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \ueb4b {{ .StashCount }}{{ end }} ",
          "foreground": "#193549",
          "powerline_symbol": "\ue0b0",
          "background": "#fffb38",
          "type": "git",
          "style": "powerline",
          "background_templates": [
            "{{ if or (.Working.Changed) (.Staging.Changed) }}#FF9248{{ end }}",
            "{{ if and (gt .Ahead 0) (gt .Behind 0) }}#ff4500{{ end }}",
            "{{ if gt .Ahead 0 }}#B388FF{{ end }}",
            "{{ if gt .Behind 0 }}#B388FF{{ end }}"
          ]
        },
        {
          "properties": {
            "cache_duration": "none",
            "fetch_version": true
          },
          "template": " \ue718 {{ if .PackageManagerIcon }}{{ .PackageManagerIcon }} {{ end }}{{ .Full }} ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "background": "#6CA35E",
          "type": "node",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "fetch_version": true
          },
          "template": " \ue626 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "background": "#8ED1F7",
          "type": "go",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "fetch_version": true
          },
          "template": " \ue624 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "background": "#4063D8",
          "type": "julia",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "display_mode": "files",
            "fetch_virtual_env": false
          },
          "template": " \ue235 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "background": "#FFDE57",
          "type": "python",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "display_mode": "files",
            "fetch_version": true
          },
          "template": " \ue791 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "background": "#AE1401",
          "type": "ruby",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "display_mode": "files",
            "fetch_version": false
          },
          "template": " \uf0e7{{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "background": "#FEAC19",
          "type": "azfunc",
          "style": "powerline"
        },
        {
          "properties": {
            "cache_duration": "none",
            "display_default": false
          },
          "template": " \ue7ad {{ .Profile }}{{ if .Region }}@{{ .Region }}{{ end }} ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "type": "aws",
          "style": "powerline",
          "background_templates": [
            "{{if contains \"default\" .Profile}}#FFA400{{end}}",
            "{{if contains \"jan\" .Profile}}#f1184c{{end}}"
          ]
        },
        {
          "properties": {
            "cache_duration": "none"
          },
          "template": " \uf0ad ",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "background": "#ffff66",
          "type": "root",
          "style": "powerline"
        },
        {
          "properties": {
            "always_enabled": true,
            "cache_duration": "none"
          },
          "trailing_diamond": "\ue0b4",
          "template": " \ue23a ",
          "foreground": "#ffffff",
          "background": "#00897b",
          "type": "status",
          "style": "diamond",
          "background_templates": [
            "{{ if gt .Code 0 }}#e91e63{{ end }}"
          ]
        }
      ]
    },
    {
      "type": "prompt",
      "alignment": "right",
      "segments": [
        {
          "properties": {
            "cache_duration": "none"
          },
          "template": "<#0077c2,transparent>\ue0b6</> \uf489 {{ .Name }} ",
          "foreground": "#ffffff",
          "background": "#0077c2",
          "type": "shell",
          "style": "diamond"
        },
        {
          "properties": {
            "always_enabled": true,
            "cache_duration": "none"
          },
          "template": " {{ .FormattedMs }}\u2800",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b2",
          "background": "#83769c",
          "type": "executiontime",
          "style": "powerline",
          "invert_powerline": true
        },
        {
          "properties": {
            "cache_duration": "none",
            "paused_icon": "\uf04c ",
            "playing_icon": "\uf04b "
          },
          "template": " \uf167 {{ .Icon }}{{ if ne .Status \"stopped\" }}{{ .Artist }} - {{ .Track }}{{ end }} ",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b2",
          "background": "#1BD760",
          "type": "ytm",
          "style": "powerline",
          "invert_powerline": true
        },
        {
          "properties": {
            "cache_duration": "none",
            "charged_icon": "\ue22f ",
            "charging_icon": "\ue234 ",
            "discharging_icon": "\ue231 "
          },
          "template": " {{ if not .Error }}{{ .Icon }}{{ .Percentage }}{{ end }}{{ .Error }}\uf295 ",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b2",
          "background": "#f36943",
          "type": "battery",
          "style": "powerline",
          "background_templates": [
            "{{if eq \"Charging\" .State.String}}#40c4ff{{end}}",
            "{{if eq \"Discharging\" .State.String}}#ff5722{{end}}",
            "{{if eq \"Full\" .State.String}}#4caf50{{end}}"
          ],
          "invert_powerline": true
        },
        {
          "properties": {
            "cache_duration": "none",
            "time_format": "15:04"
          },
          "trailing_diamond": "\ue0b4",
          "template": " {{ .CurrentDate | date .Format }} ",
          "foreground": "#111111",
          "background": "#c386f1",
          "type": "time",
          "style": "diamond",
          "invert_powerline": true
        }
      ]
    },
    {
      "type": "prompt",
      "alignment": "left",
      "segments": [
        {
          "properties": {
            "always_enabled": true,
            "cache_duration": "none"
          },
          "template": "❯ ",
          "foreground": "#ffffff",
          "type": "status",
          "style": "plain",
          "foreground_templates": [
            "{{ if gt .Code 0 }}#ff0000{{ end }}"
          ]
        }
      ],
      "newline": true
    }
  ],
  "version": 3,
  "final_space": true
}
