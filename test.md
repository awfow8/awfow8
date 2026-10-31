```mermaid
flowchart TD
    Root["📁 my-library-messenger/"]

    %% Top-level items
    Root --> CargoDir["📁 .cargo/"]
    Root --> AssetsDir["📁 assets/"]
    Root --> SrcDir["📁 src/"]
    Root --> CargoToml["📄 Cargo.toml"]
    Root --> Readme["📄 README.md"]

    %% .cargo
    CargoDir --> CargoConfig["📄 config.toml"]

    %% src/ root files & subdirectories
    SrcDir --> AppRs["📄 app.rs"]
    SrcDir --> MainRs["📄 main.rs"]
    SrcDir --> ApiDir["📁 api/"]
    SrcDir --> CompDir["📁 components/"]
    SrcDir --> DbDir["📁 db/"]
    SrcDir --> ModelsDir["📁 models/"]
    SrcDir --> StateDir["📁 state/"]
    SrcDir --> ViewsDir["📁 views/"]

    %% api/
    ApiDir --> ApiMod["📄 mod.rs"]
    ApiDir --> ChatClient["📄 chat_client.rs"]
    ApiDir --> CatalogApi["📄 catalog_api.rs"]

    %% components/
    CompDir --> CompMod["📄 mod.rs"]
    CompDir --> BookCard["📄 book_card.rs"]
    CompDir --> ChatBubble["📄 chat_bubble.rs"]
    CompDir --> Spoiler["📄 spoiler.rs"]

    %% db/
    DbDir --> DbMod["📄 mod.rs"]
    DbDir --> Cache["📄 cache.rs"]

    %% models/
    ModelsDir --> ModelsMod["📄 mod.rs"]
    ModelsDir --> Book["📄 book.rs"]
    ModelsDir --> Message["📄 message.rs"]
    ModelsDir --> User["📄 user.rs"]

    %% state/
    StateDir --> StateMod["📄 mod.rs"]
    StateDir --> AppState["📄 app_state.rs"]

    %% views/
    ViewsDir --> ViewsMod["📄 mod.rs"]
    ViewsDir --> ChatView["📄 chat_view.rs"]
    ViewsDir --> CatalogView["📄 catalog_view.rs"]
    ViewsDir --> ProfileView["📄 profile_view.rs"]

    %% Styling classes for readability
    style Root fill:#1f2937,stroke:#3b82f6,color:#fff
    style SrcDir fill:#1f2937,stroke:#10b981,color:#fff
    style CargoDir fill:#1f2937,stroke:#f59e0b,color:#fff
    style AssetsDir fill:#1f2937,stroke:#f59e0b,color:#fff
