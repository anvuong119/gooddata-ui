---
title: Theme Provider
sidebar_label: Theme Provider
copyright: (C) 2007-2020 GoodData Corporation
id: theme_provider
---

The **Theme Provider component** allows you to customize the visual style of your dashboards by applying a theme.

To be able to use the Theme Provider component, set up the `backend` and `workspace` properties in your application (see [Connecting to an Analytical Backend](02_start__connecting_backend.md#initial-setup)).

**NOTE:** Always use the Theme Provider component in the root of your application. A theme is applied globally to everything on a page. When you wrap one visual component with a `ThemeProvider`, everything else will also be themed despite not being wrapped with the `ThemeProvider`.

### Using the Theme Provider component with backend and workspace providers

When using the Theme Provider component with backend and workspace providers, you also have to set up the theme in the workspace.

```jsx
import { ThemeProvider } from "@gooddata/sdk-ui-theme-provider";

<ThemeProvider backend={backend} workspace="your-project-id">
    <Application {...}>
</ThemeProvider>
```

### Using the Theme Provider component with a custom theme

You can create properties of a custom theme, and pass the theme to the `ThemeProvider` that you added to your application.

```jsx
import { ThemeProvider } from "@gooddata/sdk-ui-theme-provider";

<ThemeProvider theme={customTheme}>
    <Application {...}/>
</ThemeProvider>

```

```jsx
import { ITheme } from "@gooddata/sdk-backend-spi";

export const customTheme: ITheme = {
  button: {
    borderRadius: "15",
    dropShadow: true,
    textCapitalization: true,
  },
  modal: {
    borderColor: "#1b4096",
    borderRadius: "5",
    borderWidth: "2",
    dropShadow: false,
    outsideBackgroundColor: "#e8cda2",
    title: {
      color: "#1b4096",
      lineColor: "#000",
    },
  },
  palette: {
    error: {
      base: "#ff2e5f",
    },
    primary: {
      base: "#eba12a",
    },
    success: {
      base: "#13ed4d",
    },
    warning: {
      base: "#ddff19",
    },
  },
  tooltip: {
    backgroundColor: "#101050",
    color: "#fff",
  },
  typography: {
    font:
      "url(https://cdn.jsdelivr.net/npm/roboto-font@0.1.0/fonts/Roboto/roboto-regular-webfont.ttf)",
    fontBold:
      "url(https://cdn.jsdelivr.net/npm/roboto-font@0.1.0/fonts/Roboto/roboto-bold-webfont.ttf)",
  },
};
```

### Example

```jsx
import { ThemeProvider } from "@gooddata/sdk-ui-theme-provider";

<div>
  <ThemeProvider>
    <BubbleHoverTrigger>
      <Button
        tagName="span"
        value="Hover over this link..."
        className="gd-button-link"
      />
      <Bubble className="bubble-primary">
        This is bubble content.
        <br />
        <Button value="Click here!" className="gd-button-positive" />
      </Bubble>
    </BubbleHoverTrigger>
  </ThemeProvider>
</div>
```