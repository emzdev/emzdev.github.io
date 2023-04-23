# Handling Local "Splitscreen" Players in an Online Session

#### Removing non-primary players from the session
There is not supported server-sided operation to remove a non-primary player ("local splitscreen player") the way 
```UGameplayStatics::RemovePlayer``` or ```UGameInstance::RemoveLocalPlayer``` would. A workaround is to make the
client-instance remove the player themselves through a client RPC.

#### Differenciating between primary players and non-primary players
Non-Primary players ("local splitscreen players") use a ```UChildConnection``` rather than the primary player's ```UNetConnection```. 
From the server, you can cast to the PlayerController's ```UChildConnection``` to see if it's a primary player or not.

``` cpp
Cast<UChildConnection>(PC->Player)
```