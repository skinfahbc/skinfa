---
name: figma-mcp
description: Use Figma MCP to inspect SKINFA designs, extract design context and assets, implement Figma frames in the codebase, and optionally send verified UI back to Figma. Use when a Figma file, frame, component, or design-system reference is provided.
---

# Figma MCP — SKINFA design-to-code workflow

Official documentation:
- https://developers.figma.com/docs/figma-mcp-server/
- https://developers.figma.com/docs/figma-mcp-server/remote-server-installation/

This file defines project workflow and guardrails. It does not install or authenticate the Figma MCP server. The MCP client must be configured separately and the user must authorize access.

## Connection
- Prefer Figma's hosted remote MCP endpoint: `https://mcp.figma.com/mcp`.
- Use a supported MCP client and complete Figma OAuth authorization.
- The Figma desktop MCP endpoint (`http://127.0.0.1:3845/mcp`) is an alternative only when the Figma desktop app is running and its server is enabled.
- Never ask the user to paste access tokens, cookies, passwords, or private authentication state into chat or repository files.
- Do not claim Figma MCP is connected unless the client confirms it and its tools are available.

## Design-to-code workflow
1. Ask for or use the exact Figma file URL or copied link to the selected frame/layer. Prefer a specific frame over an entire large file.
2. Retrieve design context before coding: hierarchy, layout, dimensions, spacing, typography, colors, variables, components, variants, constraints, and relevant assets.
3. Inspect the existing SKINFA codebase and map Figma components to existing reusable components. Reuse project conventions instead of blindly reproducing every layer.
4. Identify mismatches between the Figma design and current implementation. Preserve working product behavior and data flows.
5. Implement responsive behavior deliberately; a static desktop frame is not a complete mobile specification. Ask for mobile/tablet frames if essential details are missing, or make clearly documented responsive decisions.
6. Use actual exported assets when available. Preserve image quality, aspect ratio, transparency, and licensing/ownership context. Do not replace real product imagery with arbitrary placeholders.
7. Verify the implementation in a browser using the project's Playwright skill when available. Compare screenshots with the source frame and report differences honestly.

## Design system fidelity
- Prefer Figma variables, styles, components, and variants over hard-coded approximations.
- Keep token names and values consistent with the project when mapping them into CSS variables or theme configuration.
- Respect Persian RTL direction, typography, numerals, mixed-script content, and right-to-left component behavior.
- Match layout, spacing, type scale, radii, borders, shadows, and states with intent; do not copy pixel values mechanically when responsive constraints require adaptation.
- Do not invent missing design tokens, assets, content, or interaction states. Mark assumptions and ask when a decision materially affects the result.

## Writing back to Figma
- Only create or modify Figma canvas content when the user explicitly requests it.
- Prefer creating in drafts or a clearly named new page/frame when the destination is ambiguous.
- Before modifying an existing design, identify the exact target file and frame and summarize the intended scope if changes could overwrite existing work.
- Reuse the user's existing components and variables; do not create duplicate design systems unnecessarily.
- Do not delete, overwrite, publish, or share Figma files without explicit authorization.
- Canvas writing and some advanced features depend on Figma plan/seat permissions and the remote server; explain access limitations rather than claiming a failed tool call is a design limitation.

## Handoff and reporting
For each Figma-driven implementation, report:
- The Figma file/frame used.
- Components, variables, and assets reused.
- Assumptions made where the design was incomplete.
- Files changed in the codebase.
- Browser checks actually performed and any remaining visual differences.

Never claim pixel-perfect fidelity, a successful Figma write, or a connected MCP server unless verified.
