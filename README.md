--// Services
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera

--===[ SETTINGS ]===
local ESPEnabled = true
local AimbotEnabled = false
local TriggerbotEnabled = false
local AimKey = Enum.UserInputType.MouseButton2
local AimPart = "Head"
local FOV = 150
local Smoothness = 0.2
local HighlightColor = Color3.fromRGB(255, 0, 0)

--===[ GUI ]===
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.Name = "FullESP_AimbotGUI"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 220, 0, 230)
frame.Position = UDim2.new(0, 20, 0, 100)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0

local function createLabel(text, pos)
	local label = Instance.new("TextLabel", frame)
	label.Text = text
	label.Size = UDim2.new(1, -20, 0, 20)
	label.Position = UDim2.new(0, 10, 0, pos)
	label.TextColor3 = Color3.new(1, 1, 1)
	label.BackgroundTransparency = 1
	label.Font = Enum.Font.SourceSans
	label.TextSize = 14
	return label
end

local function createBox(default, pos)
	local box = Instance.new("TextBox", frame)
	box.Text = default
	box.Size = UDim2.new(1, -20, 0, 20)
	box.Position = UDim2.new(0, 10, 0, pos)
	box.TextColor3 = Color3.new(1, 1, 1)
	box.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	box.BorderSizePixel = 0
	return box
end

createLabel("ESP Farbe (RGB):", 5)
local rBox = createBox("255", 25)
local gBox = createBox("0", 50)
local bBox = createBox("0", 75)

local function createButton(text, pos)
	local btn = Instance.new("TextButton", frame)
	btn.Text = text
	btn.Size = UDim2.new(1, -20, 0, 30)
	btn.Position = UDim2.new(0, 10, 0, pos)
	btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	btn.TextColor3 = Color3.new(1, 1, 1)
	btn.BorderSizePixel = 0
	return btn
end

local espBtn = createButton("ESP: ON", 100)
local aimBtn = createButton("Aimbot: ON", 135)
local trigBtn =
