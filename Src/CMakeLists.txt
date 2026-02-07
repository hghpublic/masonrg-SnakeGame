target_sources(${target} PRIVATE
    CollisionHandler.cpp
    CustomEvents.cpp
    Factories.cpp
    Game.cpp
    GameText.cpp
    main.cpp
    PlayerPickups.cpp
    PlayerSnake.cpp
    TextureManager.cpp
)

add_subdirectory(Engine)