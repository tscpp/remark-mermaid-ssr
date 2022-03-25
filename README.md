# remark-mermaid-ssr

Remark plugin for rendering mermaid diagrams server-side. Installation is smoothly handled by this package; no other installations are required. Supports rendering of an additional dark mode SVGs.

This plugin uses puppeteer to launch a headless chromium browser instance to render diagrams using mermaidAPI. The codeblocks of mermaid diagrams are replaced with rendered SVGs.

## Usage

The plugin is installed as any other remark plugin, see [unified's plugin documentation](https://github.com/unifiedjs/unified#plugin).

Diagrams are written as codeblocks with the "mermaid" language.

    ```mermaid
    graph TD;
        A-->B;
        A-->C;
        B-->D;
        C-->D;
    ```

## Options

The options are **not** the same as the mermaid options. The options have been tweaked to be easier to specify. Options can always be overwritten with raw mermaid options by using the `__mermaid` and `__mermaid.__darkMode` options.

### security
```typescript
security?: 'strict' | 'loose' | 'antiscript' | 'sandbox' = 'strict'
```

Same as the mermaid option `securityLevel`. Serves as an option for the level of trust for the parsed diagram.

- `'strict'`: tags in text are encoded, script functionality is disabled.
- `'loose'`: tags in text are allowed, script functionality is enabled.
- `'antiscript'`: html tags in text are allowed, only script elements are removed, script functionality is enabled.

### theme
```typescript
theme?: string | ThemeOptions = 'default'
```

#### theme
```typescript
theme?: string = 'default'
```

#### customCss
```typescript
customCss?: string
```

#### variables
```typescript
variables?: unknown
```

### renderDark
```typescript
renderDark?: DarkOptions | boolean = false
```

Enables the additional rendering of dark mode. This will require you to define css rules for displaying the images. Rendered svgs will always (even if you have `renderDark` disabled) have either the classes `mermaid`, and `mermaid__light` or `mermaid__dark`.

```css
.mermaid.mermaid__light { display: initial; }
.mermaid.mermaid__dark { display: none; }

@media (prefers-color-scheme: dark) {
  .mermaid.mermaid__light { display: none; }
  .mermaid.mermaid__dark { display: initial; }
}
```

### logLevel
```typescript
logLevel?: LogLevel = LogLevel.Error
```

### flowchart
```typescript
flowchart?: FlowchartDiagramOptions
```

Options for flowchart diagrams.

### sequence
```typescript
sequence?: SequenceDiagramOptions
```

Options for sequence diagrams.

### gantt
```typescript
gantt?: GanttDiagramOptions
```

Options for gantt diagrams.

### journey
```typescript
journey?: JourneyDiagramOptions
```

Options for journey diagrams.

### pie
```typescript
pie?: PieChartOptions
```

Options for pie diagrams.

### requirement
```typescript
requirement?: RequirementDiagramOptions
```

Options for requirement diagrams.

### er
```typescript
er?: ErDiagramOptions
```

Options for er diagrams.

### git
```typescript
git?: GitGraphOptions
```

Options for git diagrams.

### state
```typescript
state?: StateDiagramOptions
```

Options for state diagrams.

### freeze
```typescript
freeze?: (keyof Options)[]
```

Keys in options to freeze. Same as the mermaid option `secure`.

### style
```typescript
style?: StyleOptions
```

#### fontFamily
```typescript
fontFamily?: string
```

#### maxTextSize
```typescript
maxTextSize?: number
```
