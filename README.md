

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Esperar a que PlayerGui esté listo
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

-- Si ya existe, eliminar
if PlayerGui:FindFirstChild("TestGUI") then
    PlayerGui.TestGUI:Destroy()
end

-- Crear ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "TestGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = PlayerGui -- si no aparece, probar CoreGui
-- screenGui.Parent = game:GetService("CoreGui") -- alternativa

-- Crear frame
local frame = Instance.new("Frame")
frame.Size = UDim2.fromOffset(300,200)
frame.Position = UDim2.fromScale(0.05,0.2)
frame.BackgroundColor3 = Color3.fromRGB(50,50,50)
frame.BorderSizePixel = 0
frame.Parent = screenGui

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.fromScale(1,0.2)
title.Position = UDim2.fromScale(0,0)
title.BackgroundTransparency = 1
title.Text = "SPAWNER BREIROT EXCLUSIVO"
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(255,255,255)
title.Font = Enum.Font.GothamBold
title.Parent = frame

-- Botón ejemplo
local btn = Instance.new("TextButton")
btn.Size = UDim2.fromScale(0.9,0.3)
btn.Position = UDim2.fromScale(0.05,0.5)
btn.Text = "PRUEBA"
btn.TextScaled = true
btn.BackgroundColor3 = Color3.fromRGB(100,100,100)
btn.TextColor3 = Color3.fromRGB(255,255,255)
btn.Parent = frame

btn.MouseButton1Click:Connect(function()
    print("Botón clickeado")
end)

print("GUI de prueba cargada correctamente")
