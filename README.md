# Projetos pessoais em Rust

Repositório para estudos, experimentos e projetos pessoais desenvolvidos em
[Rust](https://www.rust-lang.org/).

## Organização

- `aprendizado/` — exercícios, anotações e exemplos de estudo.
- `automacao/` — scripts e ferramentas para automatizar tarefas.
- `bibliotecas/` — crates reutilizáveis.
- `cli/` — aplicações de linha de comando.
- `experimentos/` — provas de conceito e explorações rápidas.
- `templates/` — esqueletos para iniciar novos projetos.
- `web/` — aplicações e serviços web.

## Novo projeto

Escolha a categoria adequada e crie o crate com Cargo:

```bash
cd cli
cargo new meu-projeto
```

Os arquivos `Cargo.lock` devem ser versionados para tornar builds de aplicações
reproduzíveis.
