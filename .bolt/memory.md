# Project memory

## Product intent & audience

- Personal/shared financial management app (lançamentos, cartão, contas, metas).
- Users manage finances in a "personal space" and optionally in "shared spaces" with invited members.
- User communicates in Portuguese (Brazilian); all UI and assistant responses in pt-BR.

## Brand personality & voice

- Practical, direct, confirmation-first tone for destructive actions.
- UI labels use clear pt-BR terms (e.g. "Espaço ao iniciar o app", "Sair deste espaço", "Excluir este espaço", "Limpar dados deste espaço").
- Highly destructive actions use two-step confirmation dialogs.

## Visual design & UX direction

- Settings page contains: member list, space management actions, startup-space selector, clear-space-data button.
- Member list shows all members in shared spaces; current user tagged "(você)", owner identified.
- Destructive actions (remove member, leave space, delete space, clear space data) require confirmation dialogs; clear-data uses two sequential confirmations.
- Clear-data button placed in the same area as other space actions.

## Decisions, constraints & rationale

- Supabase backend with RLS policies; prior RLS rule blocked members from seeing other members' participation rows — corrected via a secure database function.
- Only space owner can remove members, delete spaces, and clear space data; non-owners can only leave. Clear-data is enforced owner-only at the database level.
- Deleting a space cascades removal of all related data (lançamentos, cartão, contas, metas, convites).
- Clearing space data deletes all financial records (lançamentos, cartões, contas, faturas, metas, orçamentos, categorias, formas de pagamento, acertos) but preserves the space itself, members, and convites — so the app remains usable immediately.
- Vite + React framework confirmed.
- Database fixes applied carefully to avoid recursion issues previously encountered.

## Open questions & assumptions

- No explicit questions remaining from this request.
- Assumption: shared-space data isolation (per-space financial data) is enforced at the database level alongside the member-visibility fix.
- Assumption: clear-data function handles all financial tables consistently; if new tables are added later, they must be included in the function.