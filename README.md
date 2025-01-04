local tweenService = game:GetService("TweenService")
local parttween = Instance.new("Part")
parttween.Parent = workspace
parttween.Position = PositionTween
parttween.Anchored = true
parttween.Size = Vector3.new(3, 3, 3)
parttween.Material = Enum.Material.Neon
parttween.CanCollide = false
parttween.CanTouch = false
local parttweenhiglight = Instance.new("Highlight")
parttweenhiglight.Parent = parttween
parttweenhiglight.FillColor = Color3.new(0.364706, 1, 0.819608)
local tweenspeed = workspace:FindFirstChild("TweenSpeed").Value -- 100 - 500
local timetween = math.floor((game:GetService("Players")["LocalPlayer"].Character:WaitForChild("HumanoidRootPart").Position - parttween.Position).Magnitude / math.floor(tweenspeed / 2))
local tweenInfo = TweenInfo.new(timetween, Enum.EasingStyle.Linear)
local tween =
tweenService:Create(
  game:GetService("Players")["LocalPlayer"].Character:WaitForChild("HumanoidRootPart"),
	tweenInfo,
	{CFrame = CFrame.new(parttween.Position)}
)
game:GetService("Players")["LocalPlayer"].Character:WaitForChild("HumanoidRootPart").CanCollide = false
tween:Play()
game:GetService("Players")["LocalPlayer"].Character:WaitForChild("HumanoidRootPart").CanCollide = true
parttween:Destroy()
return
