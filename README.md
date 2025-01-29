local UIS = game:GetService("UserInputService")
local Lighting = game:GetService("Lighting")
local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local blackOverlay = Instance.new("Frame")
blackOverlay.Size = UDim2.new(100, 0, 100, 0)
blackOverlay.Position = UDim2.new(0, 0, 0, 0)
blackOverlay.BackgroundColor3 = Color3.new(0, 0, 0)
blackOverlay.Visible = false
blackOverlay.Parent = screenGui

local colorCorrection

local function toggleColorCorrection()
    if not colorCorrection then
        colorCorrection = Instance.new("ColorCorrectionEffect")
        colorCorrection.TintColor = Color3.new(0, 0, 0)
        colorCorrection.Brightness = -1 -- Đặt Brightness thành -1 để làm đen hoàn toàn
        colorCorrection.Parent = Lighting
        blackOverlay.Visible = true
    else
        blackOverlay.Visible = false
        colorCorrection:Destroy()
        colorCorrection = nil
    end
end

UIS.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.Minus then
        toggleColorCorrection()
    end
end)
