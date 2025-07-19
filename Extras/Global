local GetGlobal = getgenv and getgenv()

for i,v in next, game.GetChildren(game) do
    GetGlobal[v.ClassName] = v
end

GetGlobal.wait = task.wait
GetGlobal.spawn = task.spawn
GetGlobal.Player = Players.LocalPlayer
GetGlobal.Kick = Player.Kick
GetGlobal.Error = ScriptContext.Error
GetGlobal.Idled = Player.Idled
GetGlobal.MessageOut = LogService.MessageOut
GetGlobal.Stepped = RunService.Stepped
GetGlobal.RenderStepped = RunService.RenderStepped
GetGlobal.Heartbeat = RunService.Heartbeat
GetGlobal.PreRender = RunService.PreRender
GetGlobal.PreSimulation = RunService.PreSimulation
GetGlobal.PostSimulation = RunService.PostSimulation
GetGlobal.Settings = {}
GetGlobal.Verison = "v1"
GetGlobal.VG = {}
GetGlobal.IsVG = false
GetGlobal.Owner = "DekuDimz"
GetGlobal.Helper = "Bluwu"
GetGlobal.User = Instance.new("VirtualInputManager")
GetGlobal.AFK = false
GetGlobal.Character = Player.Character or Player.CharacterAdded:Wait()
GetGlobal.Protecter = Instance.new("Model", CoreGui)
GetGlobal.GameId = game.GameId
GetGlobal.AllPlayers = {}
Protecter.RobloxLocked = true

VG.Mag = function(Pos1, Pos2)
    return (Pos1.Position - Pos2.Position).Magnitude
end
-- VG.Mag(Player.Character:GetModelCFrame(), Workspace.Part1) < 50 -- true
VG.Teleport = function(Pos)
    Player.Character:PivotTo(CFrame.new(Pos))
end
-- VG.Teleport(Vector3.new(0,0,0), nil)
VG.GetNearestPlayerToBasePart = function(BasePart)
    for i,v in next, Players:GetPlayers() do
        local Radius = gethiddenproperty(v, "SimulationRadius")
        if (v.Character:GetModelCFrame().Position - BasePart.Position).Magnitude > Radius and v ~= Player then
            return true
        else
            return false
        end
    end
    return false
end
-- VG.GetNearestPlayerToBasePart(Workspace.Part1) -- true
VG.isnetworkowner = isnetworkowner or function(BasePart)
    if BasePart:IsA("BasePart") then
        local Radius = gethiddenproperty(Player, "SimulationRadius")
        if (BasePart:IsDescendantOf(Player.Character) or VG.Mag(Player.Character:GetModelCFrame(), BasePart) <= Radius) and not VG.GetNearestPlayerToBasePart(BasePart) then
            return true
        else
            return false
        end
    end
    return false
end
--VG.isnetworkowner(Player.Character.HumanoidRootPart) -- true
VG.FireConnection = function(Signal)
    if not getconnections then
        error("No getconnections detected sorry")
    else
        for i,v in next, getconnections(Signal) do
            v:Fire()
        end
    end
end
--VG.FireConnection(Player.PlayerGui.Button.MouseButton1Click)
VG.DisableConnection = function(Signal)
    if not getconnections then
        error("No getconnections Detected wth")
    else
        for i,v in next, getconnections(Signal) do
            v:Disable()
        end
    end
end

-- VG.DisableConnection(ScriptContext.Error)

VG.Tween = function(Object1, Object2, Speed, Offset, Wait)
    if Object1 and Object2 then
        local Timing = VG.Mag(Object1, Object2) / Speed
        local TweenInfo = TweenInfo.new(Timing, Enum.EasingStyle.Linear)
        local TweenSystem = TweenService:Create(Object1, TweenInfo, {CFrame = CFrame.new(Object2.Position + Offset)})
        TweenSystem:Play()
        if Wait then
            TweenSystem.Completed:Wait()
        end
    end
end
--VG.Tween(Player.Character:GetModelCFrame(), CFrame.new(0,0,0), 12, Vector3.new(0,0,0), true)

VG.ServerHop = function()
    spawn(function()
        while wait() do
            pcall(function()
                local Gay = HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. game.PlaceId .. '/servers/Public?sortOrder=Asc&limit=100'))
                for i,v in next, Gay.data do
                    if v.playing < v.maxPlayers then
                        TeleportService:TeleportToPlaceInstance(game.PlaceId, v.id, Player)
                        break
                    end
                end
            end)
            wait(4)
        end
    end)
end
-- VG.ServerHop()
VG.Rejoin = function()
    return TeleportService:Teleport(game.PlaceId, Player)
end

--VG.Rejoin()

VG.NoClip = function()
    for i,v in next, Player.Character:GetChildren() do
        if v:IsA("BasePart") then
            v.CanCollide = false
            v.Velocity = Vector3.new(0,0,0)
        end
    end
end

--VG.NoClip()

VG.GetTool = function(Name)
    if Player.Backpack:FindFirstChild(Name) then
        Player.Character.Humanoid:EquipTool(Player.Backpack:FindFirstChild(Name))
    end
end

-- VG.GetTool("Sword")

VG.FFD = function(Parent, Instance)
    return Parent:FindFirstChild(Instance, true)
end

-- if VG.FFD(Workspace, "Part") then print(true) end

VG.FFC = function(Parent, Instance)
    return Parent:FindFirstChild(Instance)
end

-- if VG.FFC(Workspace, "Part") then print("Found FirstChild Of Parent") end

VG.Wait = function(Parent, Instance)
    return Parent:WaitForChild(Instance)
end

--print(VG.Wait(Workspace))

VG.KeyPress = function(PressDown, Key, Repeated, Instance, TimesPressed)
    if User then
        User:SendKeyEvent(PressDown, Key, Repeated, Instance, TimesPressed)
    end
end
-- VG.KeyPress(true, "E", false, game, 0)

VG.GetProtecter = function()
    return Protecter
end
-- print(VG.Protecter()) -- Model, Parent CoreGui

VG.SetGuiParent = function(Gui)
    if Gui then
        Gui.RobloxLocked = true
        Gui.Parent = VG.GetProtecter()
    end
end

VG.NoClip = function()
    for i,v in next, Player.Character:GetChildren() do
        if v:IsA("BasePart") then
            v.CanCollide = false
            v.Velocity = Vector3.new(0,0,0)
        end
    end
end

--VG.NoClip()

VG.GetPos = function(Instance)
    if Instance then
        if Instance:IsA("BasePart") then
            return Instance.Position
        elseif Instance:IsA("Model") then
            return Instance:GetModelCFrame().Position
        end
    end
end

-- VG.GetPos(Character) -- Character Position

VG.PlayersTable = function()
    local Ta = {}
    for i,v in next, Players:GetPlayers() do -- why the fuck do i have to do this for dropdowns
        if not table.find(Ta, v.Name) and v ~= Player then
            table.insert(Ta, v.Name)
        end
    end
    return Ta
end
--  VG.PlayersTable() -- Table of players names

VG.GetHumanoid = function()
    return Player.Character:FindFirstChildWhichIsA("Humanoid")
end
--VG.GetHumanoid() Grabs Humanoid of Player.Character

VG.GetRoot = function()
    return Player.Character.PrimaryPart
end
--VG.GetRoot() Grabs RootPart of Character

VG.IsA= function(Parent, Instance)
    return Parent:FindFirstChildWhichIsA(Instance, true)
end
VG.SendNotification = function(Title, Text, Icon, Duration)
    return StarterGui:SetCore("SendNotification", {Title = Title, Text = Text, Icon = Icon, Duration = Duration})
end

--Loops

for i,v in next, Players:GetPlayers() do
    if v ~= Player then
        table.insert(AllPlayers, v.Name)
    end
end

Players.PlayerAdded:Connect(function(v)
    if v ~= Player then
        table.insert(AllPlayers, v.Name)
    end
end)

Players.PlayerRemoving:Connect(function(v)
    if v ~= Player then 
        local String = table.find(AllPlayers, v.Name)
        table.remove(AllPlayers, String)
    end
end)

RenderStepped:Connect(function()
    VG.GetProtecter().Name = HttpService:GenerateGUID()
end)
