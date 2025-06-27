-- GUI "Guilherme 👑" com minimizar

pcall(function() game.CoreGui["Guilherme👑"]:Destroy() end)

local player = game.Players.LocalPlayer

-- GUI principal
local gui = Instance.new("ScreenGui")
gui.Name = "Guilherme👑"
gui.ResetOnSpawn = false
gui.Parent = game:GetService("CoreGui")

-- Painel
local panel = Instance.new("Frame")
panel.Size = UDim2.new(0, 220, 0, 180)
panel.Position = UDim2.new(0, 150, 0, 60)
panel.BackgroundColor3 = Color3.fromRGB(30, 30, 140)
panel.Active = true
panel.Draggable = true
panel.Visible = true
panel.Parent = gui

Instance.new("UICorner", panel).CornerRadius = UDim.new(0, 10)

-- Título
local title = Instance.new("TextLabel")
title.Parent = panel
title.Size = UDim2.new(1, 0, 0, 30)
title.Text = "Guilherme 👑"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.BackgroundColor3 = Color3.fromRGB(15, 15, 90)
title.TextSize = 20
title.Font = Enum.Font.GothamBold
Instance.new("UICorner", title).CornerRadius = UDim.new(0, 8)

-- Botão flutuante de minimizar
local toggleButton = Instance.new("TextButton")
toggleButton.Name = "ToggleButton"
toggleButton.Size = UDim2.new(0, 40, 0, 40)
toggleButton.Position = UDim2.new(0, 20, 0, 20)
toggleButton.BackgroundColor3 = Color3.fromRGB(40, 40, 120)
toggleButton.Text = "-"
toggleButton.TextScaled = true
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.Font = Enum.Font.GothamBold
toggleButton.Parent = gui
Instance.new("UICorner", toggleButton).CornerRadius = UDim.new(0, 8)

-- Mostrar/ocultar painel
toggleButton.MouseButton1Click:Connect(function()
	panel.Visible = not panel.Visible
end)

-- Função para criar botões
local function createButton(text, yPos, color, callback)
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(0.9, 0, 0, 40)
	btn.Position = UDim2.new(0.05, 0, 0, yPos)
	btn.Text = text
	btn.BackgroundColor3 = color
	btn.TextColor3 = Color3.fromRGB(255, 255, 255)
	btn.Font = Enum.Font.GothamBold
	btn.TextSize = 18
	btn.BorderSizePixel = 0
	btn.Parent = panel
	Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
	btn.MouseButton1Click:Connect(callback)
end

-- Botões
createButton("⬆ Subir", 40, Color3.fromRGB(0, 200, 0), function()
	local char = player.Character
	if char and char:FindFirstChild("HumanoidRootPart") then
		char.HumanoidRootPart.CFrame = char.HumanoidRootPart.CFrame + Vector3.new(0, 200, 0)
	end
end)

createButton("⬇ Descer", 90, Color3.fromRGB(200, 0, 0), function()
	local char = player.Character
	if char and char:FindFirstChild("HumanoidRootPart") then
		char.HumanoidRootPart.CFrame = char.HumanoidRootPart.CFrame + Vector3.new(0, -180, 0)
	end
end)
