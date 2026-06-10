# Output links for HTML reports

When you create an HTML report, include links in the final response.

## Linux path

```text
/tmp/<report-dir>/index.html
```

## file URL

For plain Linux/browser access:

```text
file:///tmp/<report-dir>/index.html
```

When the user is on Windows reviewing a WSL report, prefer the WSL-based file URL because it is clickable from Windows browsers:

```text
file://///wsl.localhost/Ubuntu/tmp/<report-dir>/index.html
```

## Windows WSL Explorer link

If the user wants a Windows Explorer path, provide:

```text
\\wsl.localhost\Ubuntu\tmp\<report-dir>\index.html
```

If the distro may not be Ubuntu, say:

```text
\\wsl$\<DistroName>\tmp\<report-dir>\index.html
```

## Final response template

```text
Report:
/tmp/<report-dir>/index.html

WSL file:// URL:
file://///wsl.localhost/Ubuntu/tmp/<report-dir>/index.html

Windows Explorer link:
\\wsl.localhost\Ubuntu\tmp\<report-dir>\index.html
```

Keep the response short unless the user asks for details.
