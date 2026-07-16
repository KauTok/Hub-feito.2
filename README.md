--// GHOST HUB RGB | MOBILE OPTIMIZED
--// Interface futurista inspirada no Ghost Hub
--// Apenas interface visual + animações

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

-------------------------------------------------
-- GUI
-------------------------------------------------

local gui = Instance.new("ScreenGui")
gui.Name = "GhostHub"
gui.Parent = game.CoreGui
gui.ResetOnSpawn = false

-------------------------------------------------
-- RGB SYSTEM
-------------------------------------------------

local rgb = Color3.fromRGB(255,0,0)

spawn(function()
    while true do
        for h = 0,1,0.01 do
            rgb = Color3.fromHSV(h,1,1)
            task.wait()
        end
    end
end)

-------------------------------------------------
-- MAIN FRAME
-------------------------------------------------

local main = Instance.new("Frame")
main.Parent = gui
main.Size = UDim2.new(0,850,0,500)
main.Position = UDim2.new(0.5,-425,0.5,-250)
main.BackgroundColor3 = Color3.fromRGB(5,5,5)
main.BorderSizePixel = 0
main.Active = true
main.Draggable = true

local corner = Instance.new("UICorner",main)
corner.CornerRadius = UDim.new(0,20)

local stroke = Instance.new("UIStroke",main)
stroke.Thickness = 2

RunService.RenderStepped:Connect(function()
    stroke.Color = rgb
end)

-------------------------------------------------
-- TOP BAR
-------------------------------------------------

local top = Instance.new("Frame")
top.Parent = main
top.Size = UDim2.new(1,0,0,70)
top.BackgroundTransparency = 1

local title = Instance.new("TextLabel")
title.Parent = top
title.Size = UDim2.new(1,0,1,0)
title.BackgroundTransparency = 1
title.Text = "GHOST HUB"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.Font = Enum.Font.GothamBlack
title.TextScaled = true

RunService.RenderStepped:Connect(function()
    title.TextColor3 = rgb
end)

-------------------------------------------------
-- SIDE MENU
-------------------------------------------------

local menu = Instance.new("Frame")
menu.Parent = main
menu.Position = UDim2.new(0,10,0,80)
menu.Size = UDim2.new(0,180,1,-90)
menu.BackgroundColor3 = Color3.fromRGB(10,10,10)
menu.BorderSizePixel = 0

local menuCorner = Instance.new("UICorner",menu)
menuCorner.CornerRadius = UDim.new(0,15)

local layout = Instance.new("UIListLayout",menu)
layout.Padding = UDim.new(0,10)
layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
layout.VerticalAlignment = Enum.VerticalAlignment.Top

local tabs = {
    "Principal",
    "Visual",
    "Jogador",
    "Movimento",
    "Combat",
    "Mundo",
    "Scripts",
    "Console"
}

for _,v in pairs(tabs) do
    local btn = Instance.new("TextButton")
    btn.Parent = menu
    btn.Size = UDim2.new(0,160,0,45)
    btn.BackgroundColor3 = Color3.fromRGB(15,15,15)
    btn.Text = v
    btn.Font = Enum.Font.GothamBold
    btn.TextColor3 = Color3.fromRGB(255,255,255)
    btn.TextScaled = true
    btn.AutoButtonColor = false

    local bc = Instance.new("UICorner",btn)
    bc.CornerRadius = UDim.new(0,12)

    local bs = Instance.new("UIStroke",btn)

    RunService.RenderStepped:Connect(function()
        bs.Color = rgb
    end)

    btn.MouseEnter:Connect(function()
        TweenService:Create(btn,TweenInfo.new(0.2),{
            BackgroundColor3 = Color3.fromRGB(30,30,30)
        }):Play()
    end)

    btn.MouseLeave:Connect(function()
        TweenService:Create(btn,TweenInfo.new(0.2),{
            BackgroundColor3 = Color3.fromRGB(15,15,15)
        }):Play()
    end)
end

-------------------------------------------------
-- CONTENT
-------------------------------------------------

local content = Instance.new("Frame")
content.Parent = main
content.Position = UDim2.new(0,200,0,80)
content.Size = UDim2.new(1,-210,1,-90)
content.BackgroundColor3 = Color3.fromRGB(8,8,8)
content.BorderSizePixel = 0

local contentCorner = Instance.new("UICorner",content)
contentCorner.CornerRadius = UDim.new(0,15)

local contentStroke = Instance.new("UIStroke",content)

RunService.RenderStepped:Connect(function()
    contentStroke.Color = rgb
end)

-------------------------------------------------
-- WELCOME TEXT
-------------------------------------------------

local welcome = Instance.new("TextLabel")
welcome.Parent = content
welcome.Size = UDim2.new(1,0,0,60)
welcome.BackgroundTransparency = 1
welcome.Text = "BEM VINDO AO GHOST HUB"
welcome.Font = Enum.Font.GothamBlack
welcome.TextScaled = true

RunService.RenderStepped:Connect(function()
    welcome.TextColor3 = rgb
end)

-------------------------------------------------
-- FUNCTION CARDS
-------------------------------------------------

local grid = Instance.new("UIGridLayout")
grid.Parent = content
grid.CellSize = UDim2.new(0,190,0,90)
grid.CellPadding = UDim2.new(0,10,0,10)
grid.HorizontalAlignment = Enum.HorizontalAlignment.Center
grid.VerticalAlignment = Enum.VerticalAlignment.Top
grid.StartCorner = Enum.StartCorner.TopLeft

grid.FillDirectionMaxCells = 3

grid.SortOrder = Enum.SortOrder.LayoutOrder
grid:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
end)

local functionsList = {
    "Speed",
    "Fly",
    "Jump Power",
    "RGB Character",
    "Noclip",
    "FPS Boost",
    "Anti AFK",
    "UI Hide"
}

for _,name in pairs(functionsList) do
    local card = Instance.new("Frame")
    card.Parent = content
    card.BackgroundColor3 = Color3.fromRGB(12,12,12)
    card.BorderSizePixel = 0

    local cc = Instance.new("UICorner",card)
    cc.CornerRadius = UDim.new(0,12)

    local cs = Instance.new("UIStroke",card)

    RunService.RenderStepped:Connect(function()
        cs.Color = rgb
    end)

    local text = Instance.new("TextLabel")
    text.Parent = card
    text.Size = UDim2.new(1,0,0.5,0)
    text.BackgroundTransparency = 1
    text.Text = name
    text.TextColor3 = Color3.fromRGB(255,255,255)
    text.Font = Enum.Font.GothamBold
    text.TextScaled = true

    local toggle = Instance.new("TextButton")
    toggle.Parent = card
    toggle.Size = UDim2.new(0,70,0,30)
    toggle.Position = UDim2.new(0.5,-35,0.6,0)
    toggle.Text = "OFF"
    toggle.BackgroundColor3 = Color3.fromRGB(20,20,20)
    toggle.TextColor3 = Color3.fromRGB(255,255,255)
    toggle.Font = Enum.Font.GothamBold

    local tc = Instance.new("UICorner",toggle)
    tc.CornerRadius = UDim.new(1,0)

    local enabled = false

    toggle.MouseButton1Click:Connect(function()
        enabled = not enabled

        if enabled then
            toggle.Text = "ON"
            TweenService:Create(toggle,TweenInfo.new(0.2),{
                BackgroundColor3 = rgb
            }):Play()
        else
            toggle.Text = "OFF"
            TweenService:Create(toggle,TweenInfo.new(0.2),{
                BackgroundColor3 = Color3.fromRGB(20,20,20)
            }):Play()
        end
    end)
end

-------------------------------------------------
-- MOBILE BUTTON
-------------------------------------------------

local mobileBtn = Instance.new("TextButton")
mobileBtn.Parent = gui
mobileBtn.Size = UDim2.new(0,60,0,60)
mobileBtn.Position = UDim2.new(0,20,0.5,-30)
mobileBtn.Text = "☰"
mobileBtn.TextScaled = true
mobileBtn.Font = Enum.Font.GothamBlack
mobileBtn.BackgroundColor3 = Color3.fromRGB(10,10,10)
mobileBtn.TextColor3 = Color3.fromRGB(255,255,255)
mobileBtn.Active = true
mobileBtn.Draggable = true

local mc = Instance.new("UICorner",mobileBtn)
mc.CornerRadius = UDim.new(1,0)

local ms = Instance.new("UIStroke",mobileBtn)

RunService.RenderStepped:Connect(function()
    ms.Color = rgb
end)

mobileBtn.MouseButton1Click:Connect(function()
    main.Visible = not main.Visible
end)

-------------------------------------------------
-- INTRO ANIMATION
-------------------------------------------------

main.Size = UDim2.new(0,0,0,0)
main.Position = UDim2.new(0.5,0,0.5,0)

TweenService:Create(main,TweenInfo.new(0.5,Enum.EasingStyle.Back),{
    Size = UDim2.new(0,850,0,500),
    Position = UDim2.new(0.5,-425,0.5,-250)
}):Play()
