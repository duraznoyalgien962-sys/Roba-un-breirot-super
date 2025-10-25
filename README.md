
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local Title = Instance.new("TextLabel")
local SpawnButton = Instance.new("TextButton")
local EventButton = Instance.new("TextButton")

ScreenGui.Name = "GodHub"
ScreenGui.Parent = game.CoreGui

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Frame.Position = UDim2.new(0.35, 0, 0.3, 0)
Frame.Size = UDim2.new(0, 300, 0, 200)

UICorner.Parent = Frame

Title.Parent = Frame
Title.BackgroundTransparency = 1
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Text = "💀 GOD HUB 💀"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true

SpawnButton.Parent = Frame
SpawnButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
SpawnButton.Position = UDim2.new(0.15, 0, 0.35, 0)
SpawnButton.Size = UDim2.new(0.7, 0, 0.25, 0)
SpawnButton.Text = "🌪️ Spawn Breirots"
SpawnButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SpawnButton.TextScaled = true
UICorner:Clone().Parent = SpawnButton

EventButton.Parent = Frame
EventButton.BackgroundColor3 = Color3.fromRGB(80, 60, 100)
EventButton.Position = UDim2.new(0.15, 0, 0.65, 0)
EventButton.Size = UDim2.new(0.7, 0, 0.25, 0)
EventButton.Text = "🎇 Activar Eventos"
EventButton.TextColor3 = Color3.fromRGB(255, 255, 255)
EventButton.TextScaled = true
UICorner:Clone().Parent = EventButton

-- Funcionalidad
local plr = game.Players.LocalPlayer
local rep = game:GetService("ReplicatedStorage")

SpawnButton.MouseButton1Click:Connect(function()
    game.StarterGui:SetCore("SendNotification", {
        Title = "GOD HUB",
        Text = "Spawneando Breirots reales 🔥",
        Duration = 3
    })

    local nombres = {"Breirot1", "Breirot2", "Breirot3"} -- cambia estos por los nombres reales del juego

    for _, n in pairs(nombres) do
        local modelo = rep:FindFirstChild(n)
        if modelo then
            local clon = modelo:Clone()
            clon.Parent = workspace
            clon:MoveTo(plr.Character.HumanoidRootPart.Position + Vector3.new(math.random(-5,5),0,math.random(-5,5)))
        end
    end
end)

EventButton.MouseButton1Click:Connect(function()
    game.StarterGui:SetCore("SendNotification", {
        Title = "GOD HUB",
        Text = "Eventos activados 💥",
        Duration = 3
    })

    for _, ev in pairs(rep:GetChildren()) do
        if ev:IsA("RemoteEvent") then
            ev:FireServer()
        end
    end
end)
