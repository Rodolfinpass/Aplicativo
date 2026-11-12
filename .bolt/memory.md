# Project memory

## Product intent & audience

- Personal/shared financial management app (lançamentos, cartão, contas, metas).
- Users manage finances in a "personal space" and optionally in "shared spaces" with invited members.
- User communicates in Portuguese (Brazilian); all UI and assistant responses in pt-BR.

## Brand personality & voice

- Practical, direct, confirmation-first tone for destructive actions.
- UI labels use clear pt-BR terms (e.g. "Espaço ao iniciar o app", "Sair deste espaço", "Excluir este espaço").

## Visual design & UX direction

- Settings page contains: member list, space management actions, startup-space selector.
- Member list shows all members in shared spaces; current user tagged "(você)", owner identified.
- Destructive actions (remove member, leave space, delete space) require confirmation dialogs.
- Startup-space selector persists choice; app opens on selected space instead of defaulting to personal.

## Decisions, constraints & rationale

- Supabase backend with RLS policies; prior RLS rule blocked members from seeing other members' participation rows — corrected via a secure database function.
- Only space owner can remove members and delete spaces; non-owners can only leave.
- Deleting a space cascades removal of all related data (lançamentos, cartão, contas, metas, convites).
- Vite + React framework confirmed.
- Database fixes applied carefully to avoid recursion issues previously encountered.

## Open questions & assumptions

- No explicit questions remaining from this request.
- Assumption: shared-space data isolation (per-space financial data) is enforced at the database level alongside the member-visibility fix.