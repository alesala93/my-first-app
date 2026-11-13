---
paths:
  - "src/components/**"
  - "src/app/**/page.tsx"
  - "src/app/**/layout.tsx"
  - "src/hooks/**"
---

# Frontend Development Rules

## Component Source Order (MANDATORY)
1. **Project design system.** If `docs/design-system.md` exists, it is binding. Use its tokens and build the components it defines, including its own versions of elements like Badge, Tabs, Card or Navigation, following the files and mockups it points to. For interactive behaviour (dialogs, popovers, selects, focus handling) build on the shadcn/Radix primitive and style it with the design tokens.
2. **shadcn/ui.** For everything the design system does not define, check `ls src/components/ui/` first and install what is missing: `npx shadcn@latest add <name> --yes`. NEVER hand-write an element shadcn provides: Button, Input, Select, Checkbox, Switch, Dialog, Modal, Alert, Toast, Table, Tabs, Card, Badge, Dropdown, Popover, Tooltip, Navigation, Sidebar, Breadcrumb.
3. **Custom components.** ONLY business-specific compositions of the two sources above.

## Import Pattern
```tsx
import { Button } from "@/components/ui/button"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"
```

## Component Standards
- Use Tailwind CSS exclusively (no inline styles, no CSS modules); design tokens belong in the Tailwind theme (`globals.css`, `tailwind.config.ts`), not hard-coded in components
- All components must be responsive (mobile 375px, tablet 768px, desktop 1440px)
- Implement loading states, error states, and empty states
- Use semantic HTML and ARIA labels for accessibility
- Keep components small and focused
- Use TypeScript interfaces for all props

## Auth Best Practices (Supabase)
- Use `window.location.href` for post-login redirect (not `router.push`)
- Always verify `data.session` exists before redirecting
- Always reset loading state in all code paths (success, error, finally)
