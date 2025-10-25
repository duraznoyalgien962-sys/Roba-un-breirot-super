
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Lista de breirots
local breirots = {
    "tem cheese",
    "strobbery helepant",
    "garama and madundung",
    "dragón canelloni",
    "meowl",
    "lucky block secret",
    "lucky block administrador",
    "la supreme combinaciòn",
    "matteo",
    "tralalero tralala",
    "tripi tropi tropa tripa",
    "trulimero truliccina",
    "odindindun",
    "la cucaracha",
    "spooky lucky block",
    "las vaquitas saturnitas",
    "tralaledon",
    "tic tac sajur",
    "noo my examen",
    "las sis",
    "los bros",
    "los primos",
    "celularcini bisiocini",
    "los lucky blocks",
    "esok seckola"
}

-- Crear GUI
local ScreenGui = Instance.new("ScreenGui", LocalPlayer:WaitForChild("PlayerGui"))
ScreenGui.Name = "SpawnerBreirotHub"

local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0, 400, 0, 500)
Frame.Position = UDim2.new(0.5, -200, 0.5, -250)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true

local UIListLayout = Instance.new("UIListLayout", Frame)
UIListLayout.Padding = UDim.new(0,5)
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

-- Título
local Title = Instance.new("TextLabel", Frame)
Title.Size = UDim2.new(1,0,0,50)
Title.Text = "Spawner Breirot"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 24

-- Crear botones para cada breirot
for i, name in pairs(breirots) do
    local button = Instance.new("TextButton", Frame)
    button.Size = UDim2.new(1, -10, 0, 40)
    button.Text = "Spawn "..name
    button.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    button.TextColor3 = Color3.fromRGB(255,255,255)
    button.Font = Enum.Font.SourceSans
    button.TextSize = 18
    button.MouseButton1Click:Connect(function()
        -- Función para spawnear breirot
        local BreirotModel = ReplicatedStorage:FindFirstChild(name)
        if BreirotModel then
            local clone = BreirotModel:Clone()
            clone.Parent = workspace
            clone.Position = LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0,5,0)
        else
            warn("Breirot no encontrado: "..name)
        end
    end)
end

-- Eventos (ejemplo simple)
local EventButton = Instance.new("TextButton", Frame)
EventButton.Size = UDim2.new(1, -10, 0, 40)
EventButton.Text = "Activar Evento Aleatorio"
EventButton.BackgroundColor3 = Color3.fromRGB(200,50,50)
EventButton.TextColor3 = Color3.fromRGB(255,255,255)
EventButton.Font = Enum.Font.SourceSansBold
EventButton.TextSize = 18
EventButton.MouseButton1Click:Connect(function()
    local randomBreirot = breirots[math.random(1,#breirots)]
    local BreirotModel = ReplicatedStorage:FindFirstChild(randomBreirot)
    if BreirotModel then
        local clone = BreirotModel:Clone()
        clone.Parent = workspace
        clone.Position = LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0,10,0)
    end
end)
