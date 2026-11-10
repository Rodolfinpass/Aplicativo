# Project memory

## Product intent & audience

- Personal/couple finance management app (Portuguese, Brazilian audience).
- Track credit cards, invoices, transactions/lançamentos, categories/subcategories, and couple expense settlements (acertos/reembolsos).
- Supports splitting expenses between partners and tracking who paid and who owes whom.

## Brand personality & voice

- UI text in Brazilian Portuguese.
- Functional, clear, task-oriented language ("Minha despesa", "Despesa do casal", "Nova fatura", "Novo cartão").

## Visual design & UX direction

- Modal-driven workflows for creating cards, invoices, transactions, and subcategories inline.
- Numeric inputs (1–31) for card closing/due dates with clamp logic `Math.min(31, Math.max(1, parseInt(...)))`.
- Contextual inline creation: users can create cards, invoices, and subcategories without leaving the transaction modal.
- Modal stays open on error; closes only on successful save.
- Selectors for responsibility type and payer ("Quem pagou") with conditional value fields when both partners pay different amounts.

## Decisions, constraints & rationale

- Framework: Vite + React.
- Backend has a DB constraint requiring closing/due dates between 1 and 31; value 99 was invalid and removed.
- Invoices auto-fill dates based on the selected card's closing/due day.
- Unequal split payments auto-generate settlement (acerto) records in the reimbursements area.
- Build verification expected after changes.

## Open questions & assumptions

- Specific backend/DB provider (e.g., Supabase) not yet confirmed.
- No `.bolt/prompt` global instructions exist yet.
- Auth model and user/partner identity management not detailed.
- Currency formatting and locale specifics not yet specified.