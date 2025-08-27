# Sistema de Cadastro e Notificação de Eventos (Java Console)

Este projeto foi desenvolvido em **Java** como parte de atividade acadêmica, seguindo o paradigma de **Programação Orientada a Objetos (POO)**.  
O sistema permite **cadastrar usuários, cadastrar eventos, consultar eventos, confirmar ou cancelar participação e salvar eventos em arquivo** (`events.data`).

---

## 🚀 Funcionalidades
- Cadastro de usuários (mínimo de 3 atributos).
- Cadastro de eventos (nome, endereço, categoria, horário, descrição).
- Categorias de exemplo: festas, esportes, shows, palestras, etc.
- Consulta de eventos cadastrados, ordenados por data/hora.
- Identificação de eventos **já ocorridos** e **em andamento** (usando `LocalDateTime`).
- Confirmação e cancelamento de participação em eventos.
- Persistência em arquivo de texto (`events.data`), com leitura automática ao iniciar o programa.

---

## 📂 Estrutura do Projeto
src/
├── Usuario.java
├── Evento.java
├── SistemaEventos.java
└── Main.java
events.data

---

## 📌 Tecnologias
- Java 17+ (compatível também com 8+)
- Console (sem interface gráfica)
- IDEs sugeridas: Eclipse, IntelliJ, NetBeans ou Replit

---

## ▶️ Como Executar
1. Clone este repositório:
   ```bash
   git clone https://github.com/seuusuario/sistema-eventos-java.git

📊 Diagrama de Classes
classDiagram
    class Usuario {
        - int id
        - String nome
        - String email
        - String cidade
        - List<Evento> eventosConfirmados
        + participarEvento(Evento)
        + cancelarEvento(Evento)
    }

    class Evento {
        - int id
        - String nome
        - String endereco
        - String categoria
        - LocalDateTime horario
        - String descricao
        + isOcorrendoAgora()
        + isJaPassou()
        + toDataString()
        + fromDataString()
    }

    class SistemaEventos {
        - List<Usuario> usuarios
        - List<Evento> eventos
        + cadastrarUsuario(Usuario)
        + cadastrarEvento(Evento)
        + listarEventos()
        + salvarEventosNoArquivo()
        + carregarEventosDeArquivo()
    }

    class Main {
        + main()
    }

    Usuario "1" --> "*" Evento : participa
    SistemaEventos "1" --> "*" Evento
    SistemaEventos "1" --> "*" Usuario
