# LLM-Aware Comment Standard (AI Context Block Spec)

This document defines a lightweight, structured annotation format designed to help AI tools and human collaborators understand source code contextually. The goal is to improve AI-assisted development workflows by embedding relevant context, architectural details, and guidance directly in source files.

---

## 📌 Purpose
- Enable AI tools (e.g., Cursor, GitHub Copilot, Cody) to interpret developer intent, architectural constraints, and safe areas for modification.
- Provide developers with inline documentation to reduce onboarding time and improve collaboration.

---

## 🧱 AI Context Block Format
A block comment placed at the top of a source file, module, class, or function.

```ts
/* @ai-context
 * purpose: What this file/module/component is for
 * scope: Where it fits in the app or system
 * used-by: Who/what depends on this
 * dependencies: What this depends on
 * architecture: Relevant design or lifecycle details
 * safe-to-modify: What’s safe for LLMs to change
 * avoid-modifying: What should be preserved
 * notes: Any extra tips for LLMs or humans
 */
```

All fields are optional, but the more filled in, the better AI tools can assist.

---

## 💡 Example: React Component
```tsx
/* @ai-context
 * purpose: Renders the user profile settings form
 * scope: UI > Settings > Profile
 * used-by: App.tsx (routed under /settings/profile)
 * dependencies: hooks/useAuth.ts, components/InputField.tsx
 * architecture: Controlled component with internal state
 * safe-to-modify: Layout, styling, labels
 * avoid-modifying: useAuth() logic and token management
 * notes: See /docs/auth-flow.md for related auth context
 */
```

---

## 🧠 Best Practices
- Keep it close to the code — put the context block at the top of the file/module.
- Use plain language for clarity.
- Prefer consistency across your codebase (you can define templates per language).
- Reference longer docs where needed (e.g., `/docs/architecture.md`).

---

## 🛠 Tooling Suggestions (Future Work)
- Linter/Validator for `@ai-context` blocks
- Editor plugins for VSCode, Cursor, etc.
- GitHub Action to check for missing or malformed blocks

---

## 📂 Directory-Level Architecture Context (Optional)
Place a `README.md` or `architecture.md` in directories that describe:
- Folder purpose
- File relationships
- Entry points and interfaces

This can be linked in `@ai-context` via the `notes:` field.

---

## 🔄 Versioning
This is a v0.1 draft of the AI Context Block Spec. Future iterations may include structured formats like YAML or JSON-style comments.

---

## 💬 Feedback & Contributions
If you're using or improving this spec, please open an issue or PR. We’d love to see how you're applying it in the real world!
