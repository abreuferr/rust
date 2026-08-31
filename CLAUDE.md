# Convenções deste repositório

- Cada subpasta (`cli/`, `web/`, `bibliotecas/`, `automacao/`, `experimentos/`,
  `aprendizado/`) contém crates Cargo independentes. Não é um workspace: não
  existe `Cargo.toml` na raiz.
- Edition padrão dos crates: 2024.
- `Cargo.lock`: versionar em crates de aplicação (`cli/`, `web/`,
  `automacao/`, `experimentos/`, `aprendizado/`). Não versionar em
  `bibliotecas/` (convenção padrão do ecossistema Rust para crates de
  biblioteca).
- Novo projeto: `cd` na categoria certa e `cargo new nome-do-projeto`.
