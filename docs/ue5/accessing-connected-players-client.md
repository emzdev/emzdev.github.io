You can access other connected players through the **PlayerStates** framework class. PlayerStates represents a participant of a game
and they're are fully replicated to all clients unlike PlayerController (that only exist on the server and the owning client).

##GameState's PlayerArray 

The GameState comes with a PlayerArray which holds an array of all PlayerStates. The array itself isn't replicated, but 
maintained by both the server and the clients.

- When a client spawns a PlayerState, it will be added to the PlayerArray 
in ```APlayerState::PostInitializeComponents``` (if the GameState is available).

- If the GameState is not yet available, all the PlayerStates will get added once the GameState gets spawned and the 
```AGameStateBase::PostInitializeComponents``` is called.

!!! note

     There is no order in which the **PlayerStates** and the **GameState** are guaranteed to be received in on the clients (i.e. PlayerStates
		 can be spawned *before* the GameState). Be aware of this when trying to access them when the game starts.

---

###Knowing when a PlayerState has been synced
```APlayerState::PostInitializeComponents``` is called before the initial replicated values are read. In order to know when a PlayerState 
has received its initial replicated properties, you can use ```AActor::PostNetInit``` on the PlayerState

