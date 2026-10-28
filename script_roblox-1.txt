local T,UIS=game:GetService("TextChatService"),game:GetService("UserInputService")
local L=950
local g=Instance.new("ScreenGui") g.Parent=game:GetService("CoreGui") g.ResetOnSpawn=false
local f=Instance.new("Frame") f.Size=UDim2.new(0,200,0,120) f.Position=UDim2.new(0,4,0,4) f.BackgroundTransparency=1 f.Active=true f.Parent=g
local h=Instance.new("TextButton") h.Size=UDim2.new(1,0,0,14) h.BackgroundColor3=Color3.new(.25,.25,.25) h.TextColor3=Color3.new(.8,.8,.8) h.Text="≡ arraste" h.TextSize=10 h.Font=Enum.Font.Gotham h.Parent=f
local b=Instance.new("TextButton") b.Size=UDim2.new(0,55,0,30) b.Position=UDim2.new(0,0,0,18) b.BackgroundColor3=Color3.new(.1,.1,.1) b.TextColor3=Color3.new(1,1,1) b.Text="▶" b.TextSize=18 b.Parent=f
local i=Instance.new("TextBox") i.Size=UDim2.new(1,0,0,50) i.Position=UDim2.new(0,0,0,52) i.BackgroundColor3=Color3.new(.1,.1,.1) i.TextColor3=Color3.new(1,1,1) i.TextSize=3 i.TextWrapped=true i.MultiLine=true i.ClearTextOnFocus=false i.TextXAlignment=Enum.TextXAlignment.Left i.TextYAlignment=Enum.TextYAlignment.Top i.Parent=f
local c=Instance.new("TextLabel") c.Size=UDim2.new(1,0,0,12) c.Position=UDim2.new(0,0,0,106) c.BackgroundTransparency=1 c.TextColor3=Color3.new(.7,.7,.7) c.TextSize=10 c.Font=Enum.Font.Gotham c.TextXAlignment=Enum.TextXAlignment.Right c.Text="0/"..L c.Parent=f
i:GetPropertyChangedSignal("Text"):Connect(function() if #i.Text>L then i.Text=string.sub(i.Text,1,L) end local n=#i.Text c.Text=n.."/"..L c.TextColor3=n>=L and Color3.new(1,.3,.3) or n>=L*.8 and Color3.new(1,.8,.2) or Color3.new(.7,.7,.7) end)
local d,s,p=false,nil,nil
h.InputBegan:Connect(function(x) if x.UserInputType==Enum.UserInputType.MouseButton1 or x.UserInputType==Enum.UserInputType.Touch then d=true s=x.Position p=f.Position end end)
UIS.InputChanged:Connect(function(x) if d and (x.UserInputType==Enum.UserInputType.MouseMovement or x.UserInputType==Enum.UserInputType.Touch) then local q=x.Position-s f.Position=UDim2.new(p.X.Scale,p.X.Offset+q.X,p.Y.Scale,p.Y.Offset+q.Y) end end)
UIS.InputEnded:Connect(function(x) if x.UserInputType==Enum.UserInputType.MouseButton1 or x.UserInputType==Enum.UserInputType.Touch then d=false end end)
local function m() local t=Instance.new("TextLabel") t.Size=UDim2.new(0,300,0,80) t.Position=UDim2.new(.5,-150,.5,-40) t.BackgroundTransparency=1 t.TextColor3=Color3.new(1,1,1) t.TextSize=40 t.Font=Enum.Font.GothamBold t.Text="ZTU🇷🇺" t.TextStrokeTransparency=.4 t.TextStrokeColor3=Color3.new(0,0,0) t.Parent=g task.spawn(function() task.wait(2) for k=1,0,-.1 do t.TextTransparency=1-k t.TextStrokeTransparency=.4+.6*(1-k) task.wait(.03) end t:Destroy() end) end
m()
b.MouseButton1Click:Connect(function() local ch=T:FindFirstChild("TextChannels") ch=ch and ch:FindFirstChild("RBXGeneral") if ch and i.Text~="" then pcall(function() ch:SendAsync(i.Text) end) end end)
