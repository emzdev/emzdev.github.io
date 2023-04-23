The aspect ratio constraint (aka FOV scaling method) can be set in the `LocalPlayer->AspectRatioAxisConstraint`.  
The variable is of an [EAspectRatioAxisConstraint](https://docs.unrealengine.com/4.27/en-US/API/Runtime/Engine/Engine/EAspectRatioAxisConstraint/) 
type and can hold the following values:

| EAspectRatioAxisConstraint |
| ---------------- |
| `AspectRatio_MaintainYFOV` |
| `AspectRatio_MaintainXFOV` |
| `AspectRatio_MajorAxisFOV` |
| `AspectRatio_MAX` |

#### How to set the Aspect Ratio Constraint

You can set the variable through the DefaultEngine.ini or through C++.

!!! example 

	=== "DefaultEngine.ini"

		``` ini 
		[/Script/Engine.LocalPlayer]
		AspectRatioAxisConstraint = AspectRatio_MaintainYFOV
		```

	=== "C++"

		``` cpp title="MyPlayerController.cpp"
		if (GetLocalPlayer())
		{
			GetLocalPlayer()->AspectRatioAxisConstraint = EAspectRatioAxisConstraint::AspectRatio_MaintainYFOV;
		}
		```
