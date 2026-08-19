--[[
    ================================================================
    [ SCRIPT INFORMATION ]
    Project: Custom Script
    Author: OYB
    YouTube: https://www.youtube.com/channel/UCAlXXV1Hbvf7WbfXARuVtiQ
    
    [ TERMS AND CONDITIONS ]
    - You ARE allowed to use and modify this script for your own games.
    - You ARE NOT allowed to re-upload, redistribute, or claim 
      ownership of this script.
    - Removing or altering these credits is strictly prohibited.
    
    Copyright (c) 2026 OYB. All rights reserved.
    ================================================================
]]
local Config = {
    -- [1] PlatoBoost Settings
    ServiceId       = 29979
    PlatoSecret     = "0fbb4f83-edf4-4d8c-af63-242bc621ef8d", -- Your PlatoBoost Secret Key

    -- [2] Anti-Bypass / Global Secret Variable
    Secret          = "니애미표김치찌개야르", -- This makes the script ONLY run from the key script. Even if they copy the original obfuscated script to bypass the key, they won't be able to!
    
    -- [3] Scripts & Links
    MainScriptURL   = "https://raw.githubusercontent.com/dxc972962-gif/d/refs/heads/main/README.md", -- The raw URL of your main script
    
    -- [4] Social Media Settings (Set to true to show, false to hide)
    ShowDiscord     = false,
    DiscordURL      = "https://discord.gg/kT55J724BK",
    
    ShowInstagram   = false,
    InstagramURL    = "https://www.instagram.com/oyb0i/",
    
    ShowYoutube     = false,
    YoutubeURL      = "https://www.youtube.com/channel/UCAlXXV1Hbvf7WbfXARuVtiQ",

    -- [5] File System
    KeyFileName     = "Mykey.txt", -- The name of the file where the valid key will be saved for auto-login

    -- [6] GUI Management
    OldGuiName      = "Key", -- Name of the old GUI to destroy if it's already open
    MainGuiName     = "Ll고기허브 키", -- Name of the main script's GUI to check if it's already executing

    -- [7] Hub Information & UI Text
    HubName         = "get", -- The main title shown at the top of the GUI
    HubDescription  = "open" -- The text shown below the title
}

-------------------------------------------------------------------------------
--! LIBRARIES (JSON & CRYPTOGRAPHY) - DO NOT MODIFY
-------------------------------------------------------------------------------
local a=2^32;local b=a-1;local function c(d,e)local f,g=0,1;while d~=0 or e~=0 do local h,i=d%2,e%2;local j=(h+i)%2;f=f+j*g;d=math.floor(d/2)e=math.floor(e/2)g=g*2 end;return f%a end;local function k(d,e,l,...)local m;if e then d=d%a;e=e%a;m=c(d,e)if l then m=k(m,l,...)end;return m elseif d then return d%a else return 0 end end;local function n(d,e,l,...)local m;if e then d=d%a;e=e%a;m=(d+e-c(d,e))/2;if l then m=n(m,l,...)end;return m elseif d then return d%a else return b end end;local function o(p)return b-p end;local function q(d,r)if r<0 then return lshift(d,-r)end;return math.floor(d%2^32/2^r)end;local function s(p,r)if r>31 or r<-31 then return 0 end;return q(p%a,r)end;local function lshift(d,r)if r<0 then return s(d,-r)end;return d*2^r%2^32 end;local function t(p,r)p=p%a;r=r%32;local u=n(p,2^r-1)return s(p,r)+lshift(u,32-r)end;local v={0x428a2f98,0x71374491,0xb5c0fbcf,0xe9b5dba5,0x3956c25b,0x59f111f1,0x923f82a4,0xab1c5ed5,0xd807aa98,0x12835b01,0x243185be,0x550c7dc3,0x72be5d74,0x80deb1fe,0x9bdc06a7,0xc19bf174,0xe49b69c1,0xefbe4786,0x0fc19dc6,0x240ca1cc,0x2de92c6f,0x4a7484aa,0x5cb0a9dc,0x76f988da,0x983e5152,0xa831c66d,0xb00327c8,0xbf597fc7,0xc6e00bf3,0xd5a79147,0x06ca6351,0x14292967,0x27b70a85,0x2e1b2138,0x4d2c6dfc,0x53380d13,0x650a7354,0x766a0abb,0x81c2c92e,0x92722c85,0xa2bfe8a1,0xa81a664b,0xc24b8b70,0xc76c51a3,0xd192e819,0xd6990624,0xf40e3585,0x106aa070,0x19a4c116,0x1e376c08,0x2748774c,0x34b0bcb5,0x391c0cb3,0x4ed8aa4a,0x5b9cca4f,0x682e6ff3,0x748f82ee,0x78a5636f,0x84c87814,0x8cc70208,0x90befffa,0xa4506ceb,0xbef9a3f7,0xc67178f2}local function w(x)return string.gsub(x,".",function(l)return string.format("%02x",string.byte(l))end)end;local function y(z,A)local x=""for B=1,A do local C=z%256;x=string.char(C)..x;z=(z-C)/256 end;return x end;local function D(x,B)local A=0;for B=B,B+3 do A=A*256+string.byte(x,B)end;return A end;local function E(F,G)local H=64-(G+9)%64;G=y(8*G,8)F=F.."\128"..string.rep("\0",H)..G;assert(#F%64==0)return F end;local function I(J)J[1]=0x6a09e667;J[2]=0xbb67ae85;J[3]=0x3c6ef372;J[4]=0xa54ff53a;J[5]=0x510e527f;J[6]=0x9b05688c;J[7]=0x1f83d9ab;J[8]=0x5be0cd19;return J end;local function K(F,B,J)local L={}for M=1,16 do L[M]=D(F,B+(M-1)*4)end;for M=17,64 do local N=L[M-15]local O=k(t(N,7),t(N,18),s(N,3))N=L[M-2]L[M]=(L[M-16]+O+L[M-7]+k(t(N,17),t(N,19),s(N,10)))%a end;local d,e,l,P,Q,R,S,T=J[1],J[2],J[3],J[4],J[5],J[6],J[7],J[8]for B=1,64 do local O=k(t(d,2),t(d,13),t(d,22))local U=k(n(d,e),n(d,l),n(e,l))local V=(O+U)%a;local W=k(t(Q,6),t(Q,11),t(Q,25))local X=k(n(Q,R),n(o(Q),S))local Y=(T+W+X+v[B]+L[B])%a;T=S;S=R;R=Q;Q=(P+Y)%a;P=l;l=e;e=d;d=(Y+V)%a end;J[1]=(J[1]+d)%a;J[2]=(J[2]+e)%a;J[3]=(J[3]+l)%a;J[4]=(J[4]+P)%a;J[5]=(J[5]+Q)%a;J[6]=(J[6]+R)%a;J[7]=(J[7]+S)%a;J[8]=(J[8]+T)%a end;local function Z(F)F=E(F,#F)local J=I({})for B=1,#F,64 do K(F,B,J)end;return w(y(J[1],4)..y(J[2],4)..y(J[3],4)..y(J[4],4)..y(J[5],4)..y(J[6],4)..y(J[7],4)..y(J[8],4))end;local e;local l={["\\"]="\\",["\""]="\"",["\b"]="b",["\f"]="f",["\n"]="n",["\r"]="r",["\t"]="t"}local P={["/"]="/"}for Q,R in pairs(l)do P[R]=Q end;local S=function(T)return"\\"..(l[T]or string.format("u%04x",T:byte()))end;local B=function(M)return"null"end;local v=function(M,z)local _={}z=z or{}if z[M]then error("circular reference")end;z[M]=true;if rawget(M,1)~=nil or next(M)==nil then local A=0;for Q in pairs(M)do if type(Q)~="number"then error("invalid table: mixed or invalid key types")end;A=A+1 end;if A~=#M then error("invalid table: sparse array")end;for a0,R in ipairs(M)do table.insert(_,e(R,z))end;z[M]=nil;return"["..table.concat(_,",").."]"else for Q,R in pairs(M)do if type(Q)~="string"then error("invalid table: mixed or invalid key types")end;table.insert(_,e(Q,z)..":"..e(R,z))end;z[M]=nil;return"{"..table.concat(_,",").."}"end end;local g=function(M)return'"'..M:gsub('[%z\1-\31\\\"]',S)..'"'end;local a1=function(M)if M~=M or M<=-math.huge or M>=math.huge then error("unexpected number value '"..tostring(M).."'")end;return string.format("%.14g",M)end;local j={["nil"]=B,["table"]=v,["string"]=g,["number"]=a1,["boolean"]=tostring}e=function(M,z)local x=type(M)local a2=j[x]if a2 then return a2(M,z)end;error("unexpected type '"..x.."'")end;local a3=function(M)return e(M)end;local a4;local N=function(...)local _={}for a0=1,select("#",...)do _[select(a0,...)]=true end;return _ end;local L=N(" ","\t","\r","\n")local p=N(" ","\t","\r","\n","]","}",",")local a5=N("\\","/",'"',"b","f","n","r","t","u")local m=N("true","false","null")local a6={["true"]=true,["false"]=false,["null"]=nil}local a7=function(a8,a9,aa,ab)for a0=a9,#a8 do if aa[a8:sub(a0,a0)]~=ab then return a0 end end;return#a8+1 end;local ac=function(a8,a9,J)local ad=1;local ae=1;for a0=1,a9-1 do ae=ae+1;if a8:sub(a0,a0)=="\n"then ad=ad+1;ae=1 end end;error(string.format("%s at line %d col %d",J,ad,ae))end;local af=function(A)local a2=math.floor;if A<=0x7f then return string.char(A)elseif A<=0x7ff then return string.char(a2(A/64)+192,A%64+128)elseif A<=0xffff then return string.char(a2(A/4096)+224,a2(A%4096/64)+128,A%64+128)elseif A<=0x10ffff then return string.char(a2(A/262144)+240,a2(A%262144/4096)+128,a2(A%4096/64)+128,A%64+128)end;error(string.format("invalid unicode codepoint '%x'",A))end;local ag=function(ah)local ai=tonumber(ah:sub(1,4),16)local aj=tonumber(ah:sub(7,10),16)if aj then return af((ai-0xd800)*0x400+aj-0xdc00+0x10000)else return af(ai)end end;local ak=function(a8,a0)local _=""local al=a0+1;local Q=al;while al<=#a8 do local am=a8:byte(al)if am<32 then ac(a8,al,"control character in string")elseif am==92 then _=_..a8:sub(Q,al-1)al=al+1;local T=a8:sub(al,al)if T=="u"then local an=a8:match("^[dD][89aAbB]%x%x\\u%x%x%x%x",al+1)or a8:match("^%x%x%x%x",al+1)or ac(a8,al-1,"invalid unicode escape in string")_=_..ag(an)al=al+#an else if not a5[T]then ac(a8,al-1,"invalid escape char '"..T.."' in string")end;_=_..P[T]end;Q=al+1 elseif am==34 then _=_..a8:sub(Q,al-1)return _,al+1 end;al=al+1 end;ac(a8,a0,"expected closing quote for string")end;local ao=function(a8,a0)local am=a7(a8,a0,p)local ah=a8:sub(a0,am-1)local A=tonumber(ah)if not A then ac(a8,a0,"invalid number '"..ah.."'")end;return A,am end;local ap=function(a8,a0)local am=a7(a8,a0,p)local aq=a8:sub(a0,am-1)if not m[aq]then ac(a8,a0,"invalid literal '"..aq.."'")end;return a6[aq],am end;local ar=function(a8,a0)local _={}local A=1;a0=a0+1;while 1 do local am;a0=a7(a8,a0,L,true)if a8:sub(a0,a0)=="]"then a0=a0+1;break end;am,a0=a4(a8,a0)_[A]=am;A=A+1;a0=a7(a8,a0,L,true)local as=a8:sub(a0,a0)a0=a0+1;if as=="]"then break end;if as~=","then ac(a8,a0,"expected ']' or ','")end end;return _,a0 end;local at=function(a8,a0)local _={}a0=a0+1;while 1 do local au,M;a0=a7(a8,a0,L,true)if a8:sub(a0,a0)=="}"then a0=a0+1;break end;if a8:sub(a0,a0)~='"'then ac(a8,a0,"expected string for key")end;au,a0=a4(a8,a0)a0=a7(a8,a0,L,true)if a8:sub(a0,a0)~=":"then ac(a8,a0,"expected ':' after key")end;a0=a7(a8,a0+1,L,true)M,a0=a4(a8,a0)_[au]=M;a0=a7(a8,a0,L,true)local as=a8:sub(a0,a0)a0=a0+1;if as=="}"then break end;if as~=","then ac(a8,a0,"expected '}' or ','")end end;return _,a0 end;local av={['"']=ak,["0"]=ao,["1"]=ao,["2"]=ao,["3"]=ao,["4"]=ao,["5"]=ao,["6"]=ao,["7"]=ao,["8"]=ao,["9"]=ao,["-"]=ao,["t"]=ap,["f"]=ap,["n"]=ap,["["]=ar,["{"]=at}a4=function(a8,a9)local as=a8:sub(a9,a9)local a2=av[as]if a2 then return a2(a8,a9)end;ac(a8,a9,"unexpected character '"..as.."'")end;local aw=function(a8)if type(a8)~="string"then error("expected argument of type string, got "..type(a8))end;local _,a9=a4(a8,a7(a8,1,L,true))a9=a7(a8,a9,L,true)if a9<=#a8 then ac(a8,a9,"trailing garbage")end;return _ end;
local lEncode, lDecode, lDigest = a3, aw, Z;

-------------------------------------------------------------------------------
--! CORE FUNCTIONS (REQUESTS & VERIFICATION)
-------------------------------------------------------------------------------

local useNonce = true 

local function safeRequest(options)
    local req = request or http_request or syn_request or (http and http.request )
    if not req then return nil, "HTTP requests not supported" end
    local success, response = pcall(function() return req(options) end)
    if success and type(response) == "table" then 
        return response 
    else 
       
        return nil, "Connection Error: " .. tostring(response or "Unknown") 
    end
end

local fSetClipboard = setclipboard or toclipboard or function() end
local fStringChar, fToString, fOsTime, fMathRandom, fMathFloor = string.char, tostring, os.time, math.random, math.floor
local fGetHwid = gethwid or function() return game:GetService("RbxAnalyticsService"):GetClientId() end

local cachedLink, cachedTime = "", 0
local host = "https://api.platoboost.com"

local function checkConnectivity( )
    local response, err = safeRequest({Url = host .. "/public/connectivity", Method = "GET"})
    if not response or (response.StatusCode ~= 200 and response.StatusCode ~= 429) then
        host = "https://api.platoboost.net"
        local fallbackResponse, fallbackErr = safeRequest({Url = host .. "/public/connectivity", Method = "GET"})
        if not fallbackResponse then
            return false 
        end
    end
    return true
end

local function generateNonce()
    local str = ""
    for _ = 1, 16 do str = str .. fStringChar(fMathFloor(fMathRandom() * (122 - 97 + 1)) + 97) end
    return str
end

local function cacheLink()
    local isConnected = checkConnectivity()
    if not isConnected then
        return false, "Delta/Network Error! Use VPN or change Executor."
    end
    
    if cachedTime + (10*60) < fOsTime() then
        local response, err = safeRequest({
            Url = host .. "/public/start",
            Method = "POST",
            Body = lEncode({service = Config.ServiceId, identifier = lDigest(fGetHwid())}),
            Headers = {["Content-Type"] = "application/json"}
        })
        if response and response.StatusCode == 200 then
            local decoded = lDecode(response.Body)
            if decoded.success then
                cachedLink = decoded.data.url
                cachedTime = fOsTime()
                return true, cachedLink
            end
        end
        return false, err or "Server Unreachable"
    end
    return true, cachedLink
end

local function redeemKey(key)
    local nonce = generateNonce()
    local body = {identifier = lDigest(fGetHwid()), key = key}
    if useNonce then body.nonce = nonce end
    
    local response, err = safeRequest({
        Url = host .. "/public/redeem/" .. fToString(Config.ServiceId),
        Method = "POST",
        Body = lEncode(body),
        Headers = {["Content-Type"] = "application/json"}
    })
    
    if response and response.StatusCode == 200 then
        local decoded = lDecode(response.Body)
        if decoded.success and decoded.data.valid then
            if useNonce then
                if decoded.data.hash == lDigest("true" .. "-" .. nonce .. "-" .. Config.PlatoSecret) then 
                    if writefile then writefile(Config.KeyFileName, key) end
                    return true, "Success" 
                end
                return false, "Integrity Check Failed"
            end
            if writefile then writefile(Config.KeyFileName, key) end
            return true, "Success"
        end
        return false, decoded.message or "Invalid Key"
    end
    return false, err or "Server Error"
end

-------------------------------------------------------------------------------
--! GUI & MAIN SCRIPT EXECUTION
-------------------------------------------------------------------------------

local function StartMainScript()
    local player = game:GetService("Players").LocalPlayer
    local pGui = player:WaitForChild("PlayerGui")
    
    if pGui:FindFirstChild(Config.OldGuiName) then 
        pGui[Config.OldGuiName]:Destroy() 
        task.wait(0.1)
    end
    
    _G[Config.Secret] = true 
    
    loadstring(game:HttpGet(Config.MainScriptURL))()
end

local function CreateGUI()
    local player = game:GetService("Players").LocalPlayer
    local coreGui = game:GetService("CoreGui")
    local targetParent = pcall(function() return coreGui end) and coreGui or player:WaitForChild("PlayerGui")
    
    if targetParent:FindFirstChild("OYB_KeySystem") then targetParent.OYB_KeySystem:Destroy() end

    local ScreenGui = Instance.new("ScreenGui", targetParent)
    ScreenGui.Name = "OYB_KeySystem"
    ScreenGui.ResetOnSpawn = false

    local MainFrame = Instance.new("Frame", ScreenGui)
    MainFrame.Size = UDim2.new(0, 340, 0, 420)
    MainFrame.Position = UDim2.new(0.5, -170, 0.5, -210)
    MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
    MainFrame.Active = true;
    MainFrame.Draggable = true
    Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 15)
    
    local mainStroke = Instance.new("UIStroke", MainFrame)
    mainStroke.Thickness = 2;
    mainStroke.Color = Color3.fromRGB(40, 40, 40)

    local CloseBtn = Instance.new("TextButton", MainFrame)
    CloseBtn.Size = UDim2.new(0, 30, 0, 30)
    CloseBtn.Position = UDim2.new(1, -35, 0, 10)
    CloseBtn.BackgroundTransparency = 1
    CloseBtn.Text = "X"
    CloseBtn.TextColor3 = Color3.fromRGB(255, 50, 50)
    CloseBtn.Font = Enum.Font.GothamBold
    CloseBtn.TextSize = 18
    CloseBtn.ZIndex = 10
    CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)

    local Title = Instance.new("TextLabel", MainFrame)
    Title.Size = UDim2.new(1, 0, 0, 50)
    Title.Text = Config.HubName
    Title.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
    Title.TextColor3 = Color3.fromRGB(0, 170, 255)
    Title.Font = Enum.Font.GothamBold;
    Title.TextSize = 16
    Instance.new("UICorner", Title).CornerRadius = UDim.new(0, 15)

    local PromoText = Instance.new("TextLabel", MainFrame)
    PromoText.Size = UDim2.new(0.9, 0, 0, 50)
    PromoText.Position = UDim2.new(0.05, 0, 0, 50)
    PromoText.BackgroundTransparency = 1
    PromoText.Text = Config.HubDescription
    PromoText.TextColor3 = Color3.fromRGB(0, 170, 255)
    PromoText.Font = Enum.Font.GothamBold;
    PromoText.TextSize = 14
    PromoText.TextWrapped = true

    local function AddRainbowStroke(parent)
        local stroke = Instance.new("UIStroke", parent)
        stroke.Thickness = 2
        stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
        task.spawn(function()
            while task.wait() do
                local hue = tick() % 5 / 5
                stroke.Color = Color3.fromHSV(hue, 1, 1)
            end
        end)
    end

    local currentYOffset = 105

    if Config.ShowDiscord then
        local DiscordBtn = Instance.new("TextButton", MainFrame)
        DiscordBtn.Size = UDim2.new(0.85, 0, 0, 35)
        DiscordBtn.Position = UDim2.new(0.075, 0, 0, currentYOffset)
        DiscordBtn.Text = "      JOIN DISCORD"
        DiscordBtn.Font = "GothamBold";
        DiscordBtn.TextSize = 14
        DiscordBtn.BackgroundColor3 = Color3.fromRGB(88, 101, 242)
        DiscordBtn.TextColor3 = Color3.new(1, 1, 1)
        Instance.new("UICorner", DiscordBtn)
        AddRainbowStroke(DiscordBtn)

        local DiscordIcon = Instance.new("ImageLabel", DiscordBtn)
        DiscordIcon.Size = UDim2.new(0, 20, 0, 20)
        DiscordIcon.Position = UDim2.new(0.1, 0, 0.5, -10)
        DiscordIcon.BackgroundTransparency = 1
        DiscordIcon.Image = "rbxassetid://18505728201"
        
        DiscordBtn.MouseButton1Click:Connect(function()
            fSetClipboard(Config.DiscordURL)
            local Status = MainFrame:FindFirstChild("StatusLabel")
            if Status then 
                Status.Text = "Discord Link Copied!"
                Status.TextColor3 = Color3.fromRGB(88, 101, 242)
            end
            local inviteCode = string.match(Config.DiscordURL, "discord%.gg/([%w-]+)")
            if syn and syn.request and inviteCode then
                syn.request({Url = "http://localhost:1111/discord?invite=" .. inviteCode, Method = "GET"})
            end
        end)
        
        currentYOffset = currentYOffset + 45
    end

    if Config.ShowInstagram then
        local InstaBtn = Instance.new("TextButton", MainFrame)
        InstaBtn.Size = UDim2.new(0.85, 0, 0, 35)
        InstaBtn.Position = UDim2.new(0.075, 0, 0, currentYOffset)
        InstaBtn.Text = "      FOLLOW INSTAGRAM"
        InstaBtn.Font = "GothamBold";
        InstaBtn.TextSize = 14
        InstaBtn.BackgroundColor3 = Color3.fromRGB(225, 48, 108)
        InstaBtn.TextColor3 = Color3.new(1, 1, 1)
        Instance.new("UICorner", InstaBtn)
        AddRainbowStroke(InstaBtn)

        local InstaIcon = Instance.new("ImageLabel", InstaBtn)
        InstaIcon.Size = UDim2.new(0, 20, 0, 20)
        InstaIcon.Position = UDim2.new(0.1, 0, 0.5, -10)
        InstaIcon.BackgroundTransparency = 1
        InstaIcon.Image = "rbxassetid://18355586382"
        
        InstaBtn.MouseButton1Click:Connect(function()
            fSetClipboard(Config.InstagramURL)
            local Status = MainFrame:FindFirstChild("StatusLabel")
            if Status then 
                Status.Text = "Instagram Link Copied!"
                Status.TextColor3 = Color3.fromRGB(225, 48, 108)
            end
        end)
        
        currentYOffset = currentYOffset + 45
    end
    
    if Config.ShowYoutube then
        local YTBtn = Instance.new("TextButton", MainFrame)
        YTBtn.Size = UDim2.new(0.85, 0, 0, 35)
        YTBtn.Position = UDim2.new(0.075, 0, 0, currentYOffset)
        YTBtn.Text = "      SUBSCRIBE YOUTUBE"
        YTBtn.Font = "GothamBold";
        YTBtn.TextSize = 14
        YTBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
        YTBtn.TextColor3 = Color3.new(1, 1, 1)
        Instance.new("UICorner", YTBtn)
        AddRainbowStroke(YTBtn)

        local YTIcon = Instance.new("ImageLabel", YTBtn)
        YTIcon.Size = UDim2.new(0, 20, 0, 20)
        YTIcon.Position = UDim2.new(0.1, 0, 0.5, -10)
        YTIcon.BackgroundTransparency = 1
        YTIcon.Image = "rbxassetid://82532989017804"
        
        YTBtn.MouseButton1Click:Connect(function()
            fSetClipboard(Config.YoutubeURL)
            local Status = MainFrame:FindFirstChild("StatusLabel")
            if Status then
                Status.Text = "YouTube Link Copied!"
                Status.TextColor3 = Color3.fromRGB(255, 0, 0)
            end
        end)
        
        currentYOffset = currentYOffset + 45
    end

    local KeyInput = Instance.new("TextBox", MainFrame)
    KeyInput.Size = UDim2.new(0.85, 0, 0, 40)
    KeyInput.Position = UDim2.new(0.075, 0, 0, currentYOffset + 15)
    KeyInput.PlaceholderText = "Enter Key..."
    KeyInput.Text = ""
    KeyInput.Font = Enum.Font.GothamSemibold;
    KeyInput.TextSize = 14
    KeyInput.BackgroundColor3 = Color3.fromRGB(25, 25, 25);
    KeyInput.TextColor3 = Color3.new(1, 1, 1)
    Instance.new("UICorner", KeyInput)

    local VerifyBtn = Instance.new("TextButton", MainFrame)
    VerifyBtn.Size = UDim2.new(0.4, 0, 0, 40)
    VerifyBtn.Position = UDim2.new(0.075, 0, 0, currentYOffset + 65)
    VerifyBtn.Text = "VERIFY"
    VerifyBtn.Font = "GothamBold";
    VerifyBtn.TextSize = 14
    VerifyBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 255);
    VerifyBtn.TextColor3 = Color3.new(1, 1, 1)
    Instance.new("UICorner", VerifyBtn)

    local GetKeyBtn = Instance.new("TextButton", MainFrame)
    GetKeyBtn.Size = UDim2.new(0.4, 0, 0, 40)
    GetKeyBtn.Position = UDim2.new(0.525, 0, 0, currentYOffset + 65)
    GetKeyBtn.Text = "GET KEY"
    GetKeyBtn.Font = "GothamBold";
    GetKeyBtn.TextSize = 14
    GetKeyBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 35);
    GetKeyBtn.TextColor3 = Color3.new(1, 1, 1)
    Instance.new("UICorner", GetKeyBtn)

    local Status = Instance.new("TextLabel", MainFrame)
    Status.Name = "StatusLabel"
    Status.Size = UDim2.new(1, 0, 0, 30)
    Status.Position = UDim2.new(0, 0, 0, currentYOffset + 115)
    Status.BackgroundTransparency = 1
    Status.Text = "Waiting for input..."
    Status.TextColor3 = Color3.fromRGB(150, 150, 150)
    Status.Font = Enum.Font.Gotham;
    Status.TextSize = 12
    
    MainFrame.Size = UDim2.new(0, 340, 0, currentYOffset + 160)

    VerifyBtn.MouseButton1Click:Connect(function()
        local key = KeyInput.Text
        if key == "" then Status.Text = "Enter a key!"; return end
        Status.Text = "Verifying..."
        local success, msg = redeemKey(key)
        if success then
            Status.Text = "Success! Loading..."
            Status.TextColor3 = Color3.fromRGB(0, 255, 100)
            task.wait(0.5)
            ScreenGui:Destroy()
            StartMainScript()
        else
            Status.Text = msg
            Status.TextColor3 = Color3.fromRGB(255, 50, 50)
        end
    end)

    GetKeyBtn.MouseButton1Click:Connect(function()
        Status.Text = "Getting Link..."
        local success, link = cacheLink()
        if success then
            fSetClipboard(link)
            Status.Text = "Link Copied!"
            Status.TextColor3 = Color3.fromRGB(0, 170, 255)
        else
            Status.Text = tostring(link) 
            Status.TextColor3 = Color3.fromRGB(255, 100, 100)
        end
    end)

    if isfile and isfile(Config.KeyFileName) then
        local savedKey = readfile(Config.KeyFileName)
        if savedKey ~= "" then
            Status.Text = "Found saved key, verifying..."
            task.spawn(function()
                local success, msg = redeemKey(savedKey)
                if success then
                    Status.Text = "Auto-login success!"
                    Status.TextColor3 = Color3.fromRGB(0, 255, 100)
                    task.wait(0.5)
                    ScreenGui:Destroy()
                    StartMainScript()
                else
                    Status.Text = "Saved key expired or invalid."
                    Status.TextColor3 = Color3.fromRGB(255, 150, 0)
                end
            end)
        end
    end
end

local player = game:GetService("Players").LocalPlayer
local pGui = player:WaitForChild("PlayerGui")

if pGui:FindFirstChild(Config.MainGuiName) then
    StartMainScript() 
    return
end

CreateGUI()

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local Workspace = game:GetService("Workspace")
local PathfindingService = game:GetService("PathfindingService")
local VirtualUser = game:GetService("VirtualUser")
local VirtualInputManager = game:GetService("VirtualInputManager")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")

local function notify(titleText, bodyText, duration)
	pcall(function()
		game:GetService("StarterGui"):SetCore("SendNotification", {
			Title = titleText,
			Text = bodyText,
			Duration = duration or 3
		})
	end)
end

local function HookMemoryBypass()
	if getrenv and hookfunction then
		pcall(function()
			hookfunction(getrenv().gcinfo, function(...)
				return 200
			end)
		end)
	end

	local statsService = cloneref(game:GetService("Stats"))
	if statsService then
		pcall(function()
			hookfunction(statsService.GetTotalMemoryUsageMb, function(arg1, ...)
				return 50
			end)
			hookfunction(statsService.GetMemoryUsageMbForTag, function(arg1, ...)
				return 49
			end)
		end)
	end
end

local function HookMetaMethods()
	local grm = getrawmetatable(game)
	setreadonly(grm, false)
	local oldNamecall = grm.__namecall

	grm.__namecall = newcclosure(function(self, ...)
		local method = getnamecallmethod()
		local args = {...}

		if not checkcaller() then
		end

		return oldNamecall(self, ...)
	end)
end

local function HookPreloadAsync()
	local ContentProvider = game:GetService("ContentProvider")
	hookfunction(ContentProvider.PreloadAsync, function(self, assets, callback, ...)
		return
	end)
end

local function protectAndWatch(tbl, name)
	local original = tbl[name]
	if not original then return end

	pcall(function()
		setmetatable(tbl, {
			__index = tbl,
			__newindex = function(t, k, v)
				if k == name then
				else
					rawset(t, k, v)
				end
			end
		})
	end)
end

protectAndWatch(_G, "loadstring")
protectAndWatch(_G, "getgenv")

local function HookAntiBan()
    pcall(function()
        local ScriptContext = game:GetService("ScriptContext")
        if getconnections then
            for _, conn in pairs(getconnections(ScriptContext.Error)) do
                conn:Disable()
            end
        end

        local rawmeta = getrawmetatable(game)
        if rawmeta then
            setreadonly(rawmeta, false)
            local oldNC = rawmeta.__namecall
            rawmeta.__namecall = newcclosure(function(self, ...)
                local method = getnamecallmethod()
                if not checkcaller() then
                    if method == "FireServer" or method == "InvokeServer" then
                        local name = tostring(self):lower()
                        if name:find("ban") or name:find("cheat") or name:find("detect") or name:find("log") or name:find("report") then
                            return nil
                        end
                    end
                end
                return oldNC(self, ...)
            end)
        end
    end)
end

local function EnableAntiCheatBypass()
	local success, err = pcall(function()
		HookMemoryBypass()
		HookMetaMethods()
		HookPreloadAsync()
		HookAntiBan()
	end)

	if success then
		notify("Bypass Status", "Anti-Cheat Bypass Active", 4)
	else
		notify("Anti-Cheat Bypass", "Bypass Failed", 4)
	end
end

EnableAntiCheatBypass()

local autoAttack = false
local autoMagic = false
local autoTree = false
local autoMonster = false
local autoBoss = false
local autoFishing = false
local autoFishingSpot = false
local autoHeal = false
local autoDurability = false
local antiAfk = false
local loopSpeedEnabled = false

local QuizSolverConnection = nil

local customWalkSpeed = humanoid and humanoid.WalkSpeed or 16
local moveMode = "Tween"

local isJustRespawned = true
local isFlying = false

local selectedSkills = {true, false, false, false}
local skillKeyCodes = {Enum.KeyCode.One, Enum.KeyCode.Two, Enum.KeyCode.Three, Enum.KeyCode.Four}
local skillCooldowns = {1.0, 1.0, 1.0, 1.0}
local lastSkillFire = {0, 0, 0, 0}

local fishingSpotCoords = {
	Vector3.new(1074, 12, -208),
	Vector3.new(1191, 14, -198),
	Vector3.new(1274, 15, -147),
	Vector3.new(1348, 13, -116),
	Vector3.new(1593, 13, 9)
}

local monsterData = {
	["Rabbit"] = {pos = Vector3.new(351, 32, -274), level = 1},
	["Bear"] = {pos = Vector3.new(-410.98, 21.73, 220.03), level = 36},
	["Crab"] = {pos = Vector3.new(349, 28, 628), level = 27},
	["Deer"] = {pos = Vector3.new(652.25, 16.31, -44.64), level = 5},
	["Fox"] = {pos = Vector3.new(911.68, 20, 0), level = 22},
	["Skeleton"] = {pos = Vector3.new(1366, 27, -673), level = 52},
	["Snail"] = {pos = Vector3.new(358.98, 15.76, 261.77), level = 16},
	["Ice Slime"] = {pos = Vector3.new(-229, 17, -250), level = 41},
	["Wolf"] = {pos = Vector3.new(-763, 13, 530), level = 31},
	["Zombie"] = {pos = Vector3.new(-1005, 30, 268), level = 42},
	["Polar Bear"] = {pos = Vector3.new(-712, 29, -111), level = 46},
	["Snowman"] = {pos = Vector3.new(-1029, 80, -925), level = 71},
	["Snow Zombie"] = {pos = Vector3.new(-874, 88, -1013), level = 74},
	["Poison Spider"] = {pos = Vector3.new(1334, 43, -414), level = 48},
	["Mummy"] = {pos = Vector3.new(895, 40, 1060), level = 61},
	["Golem"] = {pos = Vector3.new(-254, 23, -687), level = 55},
	["Scorpion"] = {pos = Vector3.new(1743, 27, -23), level = 58},
	["Red Mummy"] = {pos = Vector3.new(1353, 21, 1033), level = 64},
	["Ghost"] = {pos = Vector3.new(-1113, 18, 809), level = 68},
	["Winter Clown"] = {pos = Vector3.new(-1015, 125, -1455), level = 77},
	["Bone Dragon"] = {pos = Vector3.new(1486, 109, 1282), level = 99}
}

local monsterList = {
	"Rabbit", "Bear", "Crab", "Deer", "Fox", "Skeleton", "Snail", "Ice Slime",
	"Wolf", "Zombie", "Polar Bear", "Snowman", "Snow Zombie", "Poison Spider", "Mummy",
	"Golem", "Scorpion", "Red Mummy", "Ghost", "Winter Clown"
}

local selectedMonsters = { ["⭐ Auto Level Match"] = false }
for _, name in ipairs(monsterList) do selectedMonsters[name] = (name == "Rabbit") end

local monsterButtons = {}
local skillButtons = {}
local isMinimized = false
local isDragging = false
local dragStart, startPos

local treeInterval = 2.6
local monsterInterval = 2.6
local MIN_INTERVAL = 0.1
local MAX_INTERVAL = 10.0

local flySpeedSetting = 80.0
local MIN_FLY_SPEED = 5.0
local MAX_FLY_SPEED = 300.0

local currentTarget = nil
local targetAttackStartTime = 0
local ignoredMonsters = {}
local zoneIndex = 1

local pathMarker = nil
local laserBeam = nil
local charAttach = nil
local targetAttach = nil

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ModernAutoGui"
screenGui.ResetOnSpawn = false
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
screenGui.Parent = playerGui

local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0.42, 0, 0.55, 0)
mainFrame.Position = UDim2.new(0.04, 0, 0.1, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
mainFrame.BorderSizePixel = 0
mainFrame.ClipsDescendants = true
mainFrame.BackgroundTransparency = 1
mainFrame.Visible = false
mainFrame.Parent = screenGui
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 8)

local stroke = Instance.new("UIStroke")
stroke.Color = Color3.fromRGB(200, 200, 200)
stroke.Thickness = 1.5
stroke.Transparency = 1
stroke.Parent = mainFrame

local function startMainHub()
	local loadingFrame = Instance.new("Frame")
	loadingFrame.Size = UDim2.new(1, 0, 1, 0)
	loadingFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
	loadingFrame.BorderSizePixel = 0
	loadingFrame.ZIndex = 10
	loadingFrame.Parent = screenGui

	local loadingText = Instance.new("TextLabel")
	loadingText.Size = UDim2.new(0, 250, 0, 40)
	loadingText.Position = UDim2.new(0.5, -125, 0.5, -20)
	loadingText.BackgroundTransparency = 1
	loadingText.Text = "Loading Hub..."
	loadingText.TextColor3 = Color3.fromRGB(255, 255, 255)
	loadingText.Font = Enum.Font.GothamBold
	loadingText.TextSize = 15
	loadingText.TextTransparency = 1
	loadingText.ZIndex = 11
	loadingText.Parent = loadingFrame

	task.spawn(function()
		TweenService:Create(loadingText, TweenInfo.new(0.5), {TextTransparency = 0}):Play()
		task.wait(1.2)
		TweenService:Create(loadingText, TweenInfo.new(0.5), {TextTransparency = 1}):Play()
		TweenService:Create(loadingFrame, TweenInfo.new(0.6), {BackgroundTransparency = 1}):Play()

		task.delay(0.4, function()
			mainFrame.Visible = true
			TweenService:Create(mainFrame, TweenInfo.new(0.5), {BackgroundTransparency = 0}):Play()
			TweenService:Create(stroke, TweenInfo.new(0.5), {Transparency = 0}):Play()
		end)
		task.delay(0.6, function() loadingFrame:Destroy() end)
	end)
end

startMainHub()

local clickButton, solveQuiz, setAutoQuizSolver, updateVisualPath, removeVisualPath

clickButton = function(button)
	if firesignal then
		firesignal(button.MouseButton1Click)
		firesignal(button.Activated)
	elseif getconnections then
		for _, conn in pairs(getconnections(button.MouseButton1Click)) do
			conn:Fire()
		end
	end
end

local function getDenseMonsterClusterPosition()
	local folder = Workspace:FindFirstChild("Monsters")
	if not folder or not rootPart then return nil end

	local playerPos = rootPart.Position
	local scanRadius = 50
	local monstersInRange = {}

	local activeTargets = {}
	if selectedMonsters["⭐ Auto Level Match"] then
		local success, pLevel = pcall(function() return player.leaderstats.Level.Value end)
		if success and pLevel then
			local closestDiff = math.huge
			local bestMobName = nil
			for mName, data in pairs(monsterData) do
				if mName ~= "Bone Dragon" then
					local diff = math.abs(data.level - pLevel)
					if diff < closestDiff then
						closestDiff = diff
						bestMobName = mName
					end
				end
			end
			if bestMobName then activeTargets[bestMobName] = true end
		end
	else
		activeTargets = selectedMonsters
	end

	for _, obj in pairs(folder:GetChildren()) do
		if obj:IsA("Model") and not ignoredMonsters[obj] then
			local hum = obj:FindFirstChildOfClass("Humanoid")
			local hrp = obj:FindFirstChild("HumanoidRootPart") or obj.PrimaryPart
			if hum and hum.Health > 0 and hrp then
				local nameplate = hrp:FindFirstChild("Nameplate")
				local monsterText = ""
				if nameplate then
					for _, child in ipairs(nameplate:GetChildren()) do
						if child:IsA("TextLabel") and child:FindFirstChildOfClass("UIStroke") then
							monsterText = child.Text
							break
						end
					end
				end

				if monsterText ~= "" then
					local cleanMonsterText = string.gsub(monsterText, "%s+", "")
					local isSelectedMatch = false
					for name, isEnabled in pairs(activeTargets) do
						if name ~= "⭐ Auto Level Match" and isEnabled then
							local cleanTargetName = string.gsub(name, "%s+", "")
							if string.find(cleanMonsterText, cleanTargetName) or string.find(cleanTargetName, cleanMonsterText) then
								isSelectedMatch = true
								break
							end
						end
					end

					if isSelectedMatch then
						local pos = obj:GetPivot().Position
						if (pos - playerPos).Magnitude <= scanRadius then
							table.insert(monstersInRange, pos)
						end
					end
				end
			end
		end
	end

	if #monstersInRange == 0 then return nil end

	local centerSum = Vector3.new(0, 0, 0)
	for _, pos in ipairs(monstersInRange) do
		centerSum = centerSum + pos
	end
	local centerPos = centerSum / #monstersInRange

	return centerPos
end

solveQuiz = function(quizGui)
	if quizGui:FindFirstChild("IsSolving") then return end
	local solveTag = Instance.new("BoolValue")
	solveTag.Name = "IsSolving"
	solveTag.Parent = quizGui

	task.spawn(function()
		local box = quizGui:WaitForChild("Box", 3)
		if not box then 
			if solveTag then solveTag:Destroy() end
			return 
		end

		local titleObj = box:WaitForChild("Title", 3)
		local optionsObj = box:WaitForChild("Options", 3)
		if not titleObj or not optionsObj then 
			if solveTag then solveTag:Destroy() end
			return 
		end

		while quizGui and quizGui.Parent do
			local isVisible = false
			if quizGui:IsA("ScreenGui") and quizGui.Enabled then
				isVisible = true
			elseif (quizGui:IsA("GuiObject") or quizGui:IsA("Frame")) and quizGui.Visible then
				isVisible = true
			end

			if not isVisible then break end

			local titleText = titleObj.Text
			local buttons = {}

			for _, child in ipairs(optionsObj:GetChildren()) do
				if child:IsA("TextButton") then
					table.insert(buttons, child)
				end
			end

			local targetButton = nil

			if not titleText:find("Color") and #buttons > 0 then
				if titleText:find("Lowest") or titleText:find("Smallest") then
					local minVal = math.huge
					for _, btn in ipairs(buttons) do
						local val = tonumber(btn.Text)
						if val and val < minVal then
							minVal = val
							targetButton = btn
						end
					end
				elseif titleText:find("Highest") or titleText:find("Largest") then
					local maxVal = -math.huge
					for _, btn in ipairs(buttons) do
						local val = tonumber(btn.Text)
						if val and val > maxVal then
							maxVal = val
							targetButton = btn
						end
					end
				elseif titleText:find("%+") then
					local num1, num2 = titleText:match("(%d+)%s*%+%s*(%d+)")
					if num1 and num2 then
						local result = tonumber(num1) + tonumber(num2)
						for _, btn in ipairs(buttons) do
							if tonumber(btn.Text) == result then
								targetButton = btn
								break
							end
						end
					end
				end
			end

			if targetButton then
				clickButton(targetButton)
				task.wait(1.0)
				break
			end

			task.wait(0.5)
		end

		if solveTag and solveTag.Parent then
			solveTag:Destroy()
		end
	end)
end

setAutoQuizSolver = function(Enabled)
	if Enabled then
		if QuizSolverConnection then QuizSolverConnection:Disconnect() end

		QuizSolverConnection = playerGui.DescendantAdded:Connect(function(descendant)
			if descendant.Name == "FishingQuizGui" then
				solveQuiz(descendant)
			end
		end)

		task.spawn(function()
			while antiAfk do
				local quizGui = nil
				
				for _, desc in ipairs(playerGui:GetDescendants()) do
					if desc.Name == "FishingQuizGui" then
						quizGui = desc
						break
					end
				end

				if quizGui then
					local isVisible = false
					if quizGui:IsA("ScreenGui") and quizGui.Enabled then
						isVisible = true
					elseif (quizGui:IsA("GuiObject") or quizGui:IsA("Frame")) and quizGui.Visible then
						isVisible = true
					end

					if isVisible and quizGui:FindFirstChild("Box") then
						solveQuiz(quizGui)
						task.wait(3.5)
					end
				end
				
				task.wait(0.5)
			end
		end)
	else
		if QuizSolverConnection then
			QuizSolverConnection:Disconnect()
			QuizSolverConnection = nil
		end
	end
end

updateVisualPath = function(targetPos)
	if not rootPart or not rootPart.Parent then return end

	if not pathMarker then
		pathMarker = Instance.new("Part")
		pathMarker.Name = "AutoPathMarker"
		pathMarker.Size = Vector3.new(4.5, 0.6, 4.5)
		pathMarker.Shape = Enum.PartType.Cylinder
		pathMarker.Material = Enum.Material.Neon
		pathMarker.Color = Color3.fromRGB(255, 255, 255)
		pathMarker.Anchored = true
		pathMarker.CanCollide = false
		pathMarker.Transparency = 0.35
		pathMarker.Parent = Workspace
	end
	pathMarker.CFrame = CFrame.new(targetPos + Vector3.new(0, 0.3, 0)) * CFrame.Angles(0, 0, math.pi/2)

	if not charAttach then
		charAttach = Instance.new("Attachment")
		charAttach.Name = "AutoLaserCharAttach"
		charAttach.Parent = rootPart
	end

	if not targetAttach then
		targetAttach = Instance.new("Attachment")
		targetAttach.Name = "AutoLaserTargetAttach"
		targetAttach.Parent = pathMarker
	end

	if not laserBeam then
		laserBeam = Instance.new("Beam")
		laserBeam.Name = "AutoPathLaserBeam"
		laserBeam.Color = ColorSequence.new(Color3.fromRGB(255, 255, 255))
		laserBeam.Width0 = 0.25
		laserBeam.Width1 = 0.25
		laserBeam.TextureMode = Enum.TextureMode.Stretch
		laserBeam.FaceCamera = true
		laserBeam.Transparency = NumberSequence.new(0.2)
		laserBeam.Attachment0 = charAttach
		laserBeam.Attachment1 = targetAttach
		laserBeam.Parent = Workspace
	end
end

removeVisualPath = function()
	if laserBeam then laserBeam:Destroy(); laserBeam = nil end
	if charAttach then charAttach:Destroy(); charAttach = nil end
	if targetAttach then targetAttach:Destroy(); targetAttach = nil end
	if pathMarker then pathMarker:Destroy(); pathMarker = nil end
end

local resizeBtn = Instance.new("TextButton")
resizeBtn.Name = "ResizeHandle"
resizeBtn.Size = UDim2.new(0, 16, 0, 16)
resizeBtn.Position = UDim2.new(1, -16, 1, -16)
resizeBtn.BackgroundTransparency = 1
resizeBtn.Text = "◢"
resizeBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
resizeBtn.TextSize = 10
resizeBtn.ZIndex = 5
resizeBtn.Parent = mainFrame

local resizing = false
local resizeStart, startSize

resizeBtn.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		resizing = true
		resizeStart = input.Position
		startSize = mainFrame.AbsoluteSize
	end
end)

UserInputService.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		resizing = false
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if resizing and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
		local delta = input.Position - resizeStart
		local newW = math.clamp(startSize.X + delta.X, 180, 400)
		local newH = math.clamp(startSize.Y + delta.Y, 200, 500)
		mainFrame.Size = UDim2.new(0, newW, 0, newH)
	end
end)

local header = Instance.new("Frame")
header.Size = UDim2.new(1, 0, 0, 32)
header.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
header.BorderSizePixel = 0
header.Parent = mainFrame
Instance.new("UICorner", header).CornerRadius = UDim.new(0, 8)

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -55, 1, 0)
title.Position = UDim2.new(0, 8, 0, 0)
title.BackgroundTransparency = 1
title.Text = "Main Hub"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 11
title.TextXAlignment = Enum.TextXAlignment.Left
title.Parent = header

local minimizeBtn = Instance.new("TextButton")
minimizeBtn.Size = UDim2.new(0, 22, 0, 22)
minimizeBtn.Position = UDim2.new(1, -48, 0.5, -11)
minimizeBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
minimizeBtn.Text = "−"
minimizeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
minimizeBtn.Font = Enum.Font.GothamBold
minimizeBtn.TextSize = 13
minimizeBtn.Parent = header
Instance.new("UICorner", minimizeBtn).CornerRadius = UDim.new(0, 4)

local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 22, 0, 22)
closeBtn.Position = UDim2.new(1, -24, 0.5, -11)
closeBtn.BackgroundColor3 = Color3.fromRGB(120, 30, 30)
closeBtn.Text = "×"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.TextSize = 13
closeBtn.Parent = header
Instance.new("UICorner", closeBtn).CornerRadius = UDim.new(0, 4)

local content = Instance.new("ScrollingFrame")
content.Size = UDim2.new(1, 0, 1, -32)
content.Position = UDim2.new(0, 0, 0, 32)
content.BackgroundTransparency = 1
content.CanvasSize = UDim2.new(0, 0, 0, 0)
content.ScrollBarThickness = 2
content.ScrollBarImageColor3 = Color3.fromRGB(150, 150, 150)
content.Parent = mainFrame

local uiPadding = Instance.new("UIPadding")
uiPadding.PaddingLeft = UDim.new(0, 8)
uiPadding.PaddingRight = UDim.new(0, 8)
uiPadding.PaddingTop = UDim.new(0, 5)
uiPadding.PaddingBottom = UDim.new(0, 5)
uiPadding.Parent = content

local uiLayout = Instance.new("UIListLayout")
uiLayout.SortOrder = Enum.SortOrder.LayoutOrder
uiLayout.Padding = UDim.new(0, 4)
uiLayout.Parent = content

uiLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
	content.CanvasSize = UDim2.new(0, 0, 0, uiLayout.AbsoluteContentSize.Y + 12)
end)

local toggleIndex = 0
local function createModernToggle(text, layoutOrder, callback)
	toggleIndex = toggleIndex + 1
	local isEven = (toggleIndex % 2 == 0)
	
	local bgDefault = isEven and Color3.fromRGB(45, 45, 45) or Color3.fromRGB(25, 25, 25)
	local textDefault = isEven and Color3.fromRGB(220, 220, 220) or Color3.fromRGB(180, 180, 180)
	
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(1, 0, 0, 26)
	btn.BackgroundColor3 = bgDefault
	btn.Text = " " .. text
	btn.TextColor3 = textDefault
	btn.Font = Enum.Font.GothamMedium
	btn.TextSize = 10
	btn.TextXAlignment = Enum.TextXAlignment.Left
	btn.LayoutOrder = layoutOrder
	btn.Parent = content
	Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 5)

	local indicator = Instance.new("Frame")
	indicator.Size = UDim2.new(0, 5, 0, 5)
	indicator.Position = UDim2.new(1, -12, 0.5, -2.5)
	indicator.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
	indicator.Parent = btn
	Instance.new("UICorner", indicator).CornerRadius = UDim.new(1, 0)

	local active = false
	btn.MouseButton1Click:Connect(function()
		active = not active
		if active then
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(220, 220, 220), TextColor3 = Color3.fromRGB(0, 0, 0)}):Play()
			TweenService:Create(indicator, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(0, 0, 0)}):Play()
		else
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = bgDefault, TextColor3 = textDefault}):Play()
			TweenService:Create(indicator, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(100, 100, 100)}):Play()
		end
		callback(active)
	end)
	return btn
end

local startTreeFarm, startMonsterFarm, startFishingSpotClaim, moveToTarget

createModernToggle("Auto Melee Attack", 1, function(state) autoAttack = state end)
createModernToggle("Auto Skill (Selected)", 2, function(state) autoMagic = state end)
createModernToggle("Auto Move Trees", 3, function(state)
	autoTree = state
	if autoTree then startTreeFarm() else removeVisualPath() end
end)
createModernToggle("Auto Farm Monsters", 4, function(state)
	autoMonster = state
	if autoMonster or autoBoss then startMonsterFarm() else removeVisualPath() end
end)
createModernToggle("🔥 Priority Boss Farm (Bone Dragon)", 5, function(state)
	autoBoss = state
	if autoBoss then
		currentTarget = nil
		startMonsterFarm()
	elseif not autoMonster then
		removeVisualPath()
	end
end)
createModernToggle("🎣 Auto Fishing (E Timing)", 6, function(state) autoFishing = state end)
createModernToggle("📍 Auto Claim Fishing Spot", 7, function(state)
	autoFishingSpot = state
	if autoFishingSpot then startFishingSpotClaim() else removeVisualPath() end
end)
createModernToggle("Auto Heal R Key (HP <= 20%)", 8, function(state) autoHeal = state end)
createModernToggle("Auto Durability (Whetstone Equipped)", 9, function(state) autoDurability = state end)

createModernToggle("Anti-AFK System", 10, function(state)
	antiAfk = state
	setAutoQuizSolver(state)
end)

createModernToggle("Loop Speed Toggle", 11, function(state) loopSpeedEnabled = state end)

local targetPlayerName = ""

local targetInputFrame = Instance.new("Frame")
targetInputFrame.Size = UDim2.new(1, 0, 0, 26)
targetInputFrame.BackgroundTransparency = 1
targetInputFrame.LayoutOrder = 11.5
targetInputFrame.Parent = content

local targetTextBox = Instance.new("TextBox")
targetTextBox.Size = UDim2.new(0.7, -2, 1, 0)
targetTextBox.Position = UDim2.new(0, 0, 0, 0)
targetTextBox.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
targetTextBox.Text = ""
targetTextBox.PlaceholderText = "Target username..."
targetTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
targetTextBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
targetTextBox.Font = Enum.Font.Gotham
targetTextBox.TextSize = 9
targetTextBox.Parent = targetInputFrame
Instance.new("UICorner", targetTextBox).CornerRadius = UDim.new(0, 5)

targetTextBox:GetPropertyChangedSignal("Text"):Connect(function()
    targetPlayerName = targetTextBox.Text
end)

local targetTpBtn = Instance.new("TextButton")
targetTpBtn.Size = UDim2.new(0.3, 0, 1, 0)
targetTpBtn.Position = UDim2.new(0.7, 2, 0, 0)
targetTpBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
targetTpBtn.Text = "Target TP"
targetTpBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
targetTpBtn.Font = Enum.Font.GothamBold
targetTpBtn.TextSize = 9
targetTpBtn.Parent = targetInputFrame
Instance.new("UICorner", targetTpBtn).CornerRadius = UDim.new(0, 5)

targetTpBtn.MouseButton1Click:Connect(function()
    if targetPlayerName ~= "" then
        for _, p in pairs(Players:GetPlayers()) do
            if p ~= player and (p.Name:lower():find(targetPlayerName:lower()) or p.DisplayName:lower():find(targetPlayerName:lower())) then
                if p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
                    moveToTarget(p.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 3))
                    break
                end
            end
        end
    end
end)

local skillLabel = Instance.new("TextLabel")
skillLabel.Size = UDim2.new(1, 0, 0, 15)
skillLabel.BackgroundTransparency = 1
skillLabel.Text = "Select Skill Slots"
skillLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
skillLabel.Font = Enum.Font.GothamBold
skillLabel.TextSize = 9
skillLabel.TextXAlignment = Enum.TextXAlignment.Left
skillLabel.LayoutOrder = 12
skillLabel.Parent = content

local skillFrame = Instance.new("Frame")
skillFrame.Size = UDim2.new(1, 0, 0, 22)
skillFrame.BackgroundTransparency = 1
skillFrame.LayoutOrder = 13
skillFrame.Parent = content

for i = 1, 4 do
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(0.23, 0, 1, 0)
	btn.Position = UDim2.new(0.25 * (i-1), 0, 0, 0)
	btn.BackgroundColor3 = (i == 1) and Color3.fromRGB(220, 220, 220) or Color3.fromRGB(35, 35, 35)
	btn.Text = "Skill " .. tostring(i)
	btn.TextColor3 = (i == 1) and Color3.fromRGB(0, 0, 0) or Color3.fromRGB(200, 200, 200)
	btn.Font = Enum.Font.GothamBold
	btn.TextSize = 9
	btn.Parent = skillFrame
	Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 4)

	skillButtons[i] = btn

	btn.MouseButton1Click:Connect(function()
		selectedSkills[i] = not selectedSkills[i]
		if selectedSkills[i] then
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(220, 220, 220), TextColor3 = Color3.fromRGB(0, 0, 0)}):Play()
		else
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(35, 35, 35), TextColor3 = Color3.fromRGB(200, 200, 200)}):Play()
		end
	end)
end

local function createSlider(labelText, minV, maxV, defaultVal, isInteger, layoutOrder, callback)
	local container = Instance.new("Frame")
	container.Size = UDim2.new(1, 0, 0, 34)
	container.BackgroundTransparency = 1
	container.LayoutOrder = layoutOrder
	container.Parent = content

	local label = Instance.new("TextLabel")
	label.Size = UDim2.new(1, 0, 0, 15)
	label.BackgroundTransparency = 1
	label.Text = labelText .. string.format(isInteger and ": %d" or ": %.1fs", defaultVal)
	label.TextColor3 = Color3.fromRGB(200, 200, 200)
	label.Font = Enum.Font.GothamBold
	label.TextSize = 9
	label.TextXAlignment = Enum.TextXAlignment.Left
	label.Parent = container

	local track = Instance.new("Frame")
	track.Size = UDim2.new(1, 0, 0, 4)
	track.Position = UDim2.new(0, 0, 0, 20)
	track.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	track.BorderSizePixel = 0
	track.Parent = container
	Instance.new("UICorner", track).CornerRadius = UDim.new(1, 0)

	local fill = Instance.new("Frame")
	fill.Size = UDim2.new((defaultVal - minV)/(maxV - minV), 0, 1, 0)
	fill.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	fill.BorderSizePixel = 0
	fill.Parent = track
	Instance.new("UICorner", fill).CornerRadius = UDim.new(1, 0)

	local handle = Instance.new("TextButton")
	handle.Size = UDim2.new(0, 10, 0, 10)
	handle.Position = UDim2.new(fill.Size.X.Scale, -5, 0.5, -5)
	handle.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
	handle.Text = ""
	handle.AutoButtonColor = false
	handle.Parent = track
	Instance.new("UICorner", handle).CornerRadius = UDim.new(1, 0)

	local dragging = false
	handle.MouseButton1Down:Connect(function() dragging = true end)
	UserInputService.InputEnded:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = false
		end
	end)
	UserInputService.InputChanged:Connect(function(input)
		if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
			local p, s = track.AbsolutePosition, track.AbsoluteSize
			local ratio = math.clamp((UserInputService:GetMouseLocation().X - p.X) / s.X, 0, 1)
			fill.Size = UDim2.new(ratio, 0, 1, 0)
			handle.Position = UDim2.new(ratio, -5, 0.5, -5)

			local val = minV + (maxV - minV) * ratio
			if isInteger then
				val = math.floor(val + 0.5)
				label.Text = labelText .. string.format(": %d", val)
			else
				val = math.floor(val * 10) / 10
				label.Text = labelText .. string.format(": %.1fs", val)
			end
			callback(val)
		end
	end)
end

createSlider("Tree Farm Interval", MIN_INTERVAL, MAX_INTERVAL, 2.6, false, 14, function(v) treeInterval = v end)
createSlider("Monster Farm Interval", MIN_INTERVAL, MAX_INTERVAL, 2.6, false, 15, function(v) monsterInterval = v end)
createSlider("Fly Speed", MIN_FLY_SPEED, MAX_FLY_SPEED, 80.0, true, 16, function(v) flySpeedSetting = v end)
createSlider("WalkSpeed Value", 16, 500, customWalkSpeed, true, 17, function(v) customWalkSpeed = v end)

local dropdownHeader = Instance.new("TextButton")
dropdownHeader.Size = UDim2.new(1, 0, 0, 26)
dropdownHeader.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
dropdownHeader.Text = " ▶ Select Target Monster"
dropdownHeader.TextColor3 = Color3.fromRGB(220, 220, 220)
dropdownHeader.Font = Enum.Font.GothamBold
dropdownHeader.TextSize = 10
dropdownHeader.TextXAlignment = Enum.TextXAlignment.Left
dropdownHeader.LayoutOrder = 20
dropdownHeader.Parent = content

local dropdownContainer = Instance.new("Frame")
dropdownContainer.Size = UDim2.new(1, 0, 0, 230)
dropdownContainer.BackgroundTransparency = 1
dropdownContainer.Visible = false
dropdownContainer.LayoutOrder = 21
dropdownContainer.Parent = content

local levelMatchBtn = Instance.new("TextButton")
levelMatchBtn.Size = UDim2.new(1, 0, 0, 22)
levelMatchBtn.Position = UDim2.new(0, 0, 0, 0)
levelMatchBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
levelMatchBtn.Text = "⭐ Auto Level Match"
levelMatchBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
levelMatchBtn.Font = Enum.Font.GothamBold
levelMatchBtn.TextSize = 9
levelMatchBtn.Parent = dropdownContainer
Instance.new("UICorner", levelMatchBtn).CornerRadius = UDim.new(0, 4)
monsterButtons["⭐ Auto Level Match"] = levelMatchBtn

for i, name in ipairs(monsterList) do
	local btn = Instance.new("TextButton")
	local row = math.floor((i-1) / 3)
	local col = (i-1) % 3

	btn.Size = UDim2.new(0.31, 0, 0, 20)
	btn.Position = UDim2.new(col * 0.34, 0, 0, 25 + row * 24)
	btn.BackgroundColor3 = (name == "Rabbit") and Color3.fromRGB(220, 220, 220) or Color3.fromRGB(35, 35, 35)
	btn.Text = name
	btn.TextColor3 = (name == "Rabbit") and Color3.fromRGB(0, 0, 0) or Color3.fromRGB(200, 200, 200)
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 9
	btn.Parent = dropdownContainer
	Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 4)
	monsterButtons[name] = btn
end

dropdownHeader.MouseButton1Click:Connect(function()
	dropdownContainer.Visible = not dropdownContainer.Visible
	if dropdownContainer.Visible then
		dropdownHeader.Text = " ▼ Select Target Monster"
	else
		dropdownHeader.Text = " ▶ Select Target Monster"
	end
end)

for name, btn in pairs(monsterButtons) do
	btn.MouseButton1Click:Connect(function()
		selectedMonsters[name] = not selectedMonsters[name]
		if selectedMonsters[name] then
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(220, 220, 220), TextColor3 = Color3.fromRGB(0, 0, 0)}):Play()
		else
			TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(35, 35, 35), TextColor3 = Color3.fromRGB(200, 200, 200)}):Play()
		end
	end)
end

local npcHeader = Instance.new("TextButton")
npcHeader.Size = UDim2.new(1, 0, 0, 26)
npcHeader.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
npcHeader.Text = " ▶ NPC Teleport"
npcHeader.TextColor3 = Color3.fromRGB(220, 220, 220)
npcHeader.Font = Enum.Font.GothamBold
npcHeader.TextSize = 10
npcHeader.TextXAlignment = Enum.TextXAlignment.Left
npcHeader.LayoutOrder = 22
npcHeader.Parent = content
Instance.new("UICorner", npcHeader).CornerRadius = UDim.new(0, 5)

local npcContainer = Instance.new("ScrollingFrame")
npcContainer.Size = UDim2.new(1, 0, 0, 100)
npcContainer.BackgroundTransparency = 1
npcContainer.Visible = false
npcContainer.LayoutOrder = 23
npcContainer.CanvasSize = UDim2.new(0, 0, 0, 0)
npcContainer.ScrollBarThickness = 2
npcContainer.Parent = content

local npcLayout = Instance.new("UIListLayout")
npcLayout.SortOrder = Enum.SortOrder.LayoutOrder
npcLayout.Padding = UDim.new(0, 3)
npcLayout.Parent = npcContainer

npcLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
	npcContainer.CanvasSize = UDim2.new(0, 0, 0, npcLayout.AbsoluteContentSize.Y + 6)
end)

local function updateNpcList()
	for _, child in pairs(npcContainer:GetChildren()) do
		if child:IsA("TextButton") then child:Destroy() end
	end

	local folder = Workspace:FindFirstChild("VillageNPCs") or Workspace:FindFirstChild("NPCs") or Workspace
	if not folder then return end

	local count = 0
	for _, npc in pairs(folder:GetChildren()) do
		if npc:IsA("Model") and npc ~= character and npc:FindFirstChildOfClass("Humanoid") then
			count = count + 1
			local btn = Instance.new("TextButton")
			btn.Size = UDim2.new(1, 0, 0, 22)
			btn.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			btn.Text = " 📍 " .. npc.Name .. " (TP)"
			btn.TextColor3 = Color3.fromRGB(200, 200, 200)
			btn.Font = Enum.Font.Gotham
			btn.TextSize = 9
			btn.TextXAlignment = Enum.TextXAlignment.Left
			btn.LayoutOrder = count
			btn.Parent = npcContainer
			Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 4)

			btn.MouseButton1Click:Connect(function()
				if rootPart and rootPart.Parent then
					local pivot = npc:GetPivot()
					local pos = pivot and pivot.Position or (npc.PrimaryPart and npc.PrimaryPart.Position)
					if pos then moveToTarget(CFrame.new(pos + Vector3.new(0, 3, 0))) end
				end
			end)
		end
	end
	npcContainer.Size = UDim2.new(1, 0, 0, math.clamp(count * 25, 25, 110))
end

npcHeader.MouseButton1Click:Connect(function()
	local visible = not npcContainer.Visible
	npcContainer.Visible = visible
	if visible then
		npcHeader.Text = " ▼ NPC Teleport"
		updateNpcList()
	else
		npcHeader.Text = " ▶ NPC Teleport"
	end
end)

minimizeBtn.MouseButton1Click:Connect(function()
	isMinimized = not isMinimized
	if isMinimized then
		TweenService:Create(mainFrame, TweenInfo.new(0.25), {Size = UDim2.new(0.42, 0, 0, 32)}):Play()
		content.Visible = false
		minimizeBtn.Text = "+"
	else
		content.Visible = true
		TweenService:Create(mainFrame, TweenInfo.new(0.3), {Size = UDim2.new(0.42, 0, 0.55, 0)}):Play()
		minimizeBtn.Text = "−"
	end
end)

closeBtn.MouseButton1Click:Connect(function() screenGui:Destroy() end)

header.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		isDragging = true
		dragStart = input.Position
		startPos = mainFrame.Position
	end
end)

header.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		isDragging = false
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if isDragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
		local delta = input.Position - dragStart
		mainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
	end
end)

local function flyToTarget(targetCFrame)
	if not rootPart or not rootPart.Parent then return end
	isFlying = true

	local targetPos = targetCFrame.Position
	local adjustedY = targetPos.Y
	if humanoid and humanoid.HipHeight then
		adjustedY = adjustedY + humanoid.HipHeight + 1.5
	else
		adjustedY = adjustedY + 3.5
	end
	
	local safeTargetCFrame = CFrame.new(targetPos.X, adjustedY, targetPos.Z) * targetCFrame.Rotation
	updateVisualPath(safeTargetCFrame.Position)

	local distance = (safeTargetCFrame.Position - rootPart.Position).Magnitude
	local travelTime = math.clamp(distance / flySpeedSetting, 0.1, 10.0)
	local tweenInfo = TweenInfo.new(travelTime, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
	local tween = TweenService:Create(rootPart, tweenInfo, {CFrame = safeTargetCFrame})

	tween:Play()
	tween.Completed:Wait()

	removeVisualPath()
	isFlying = false
end

moveToTarget = function(targetCFrame)
	if not rootPart or not rootPart.Parent or isFlying then return end
	flyToTarget(targetCFrame)
end

local function getClosestTree()
	local closest = nil
	local closestDist = math.huge
	local success, folder = pcall(function() return Workspace.Decorations.Trees.AutumnOak end)
	if not success or not folder or not rootPart then return nil end

	local playerPos = rootPart.Position
	local successInternal, children = pcall(function() return folder:GetChildren() end)
	if not successInternal or not children then return nil end

	for _, obj in pairs(children) do
		if obj:IsA("Model") then
			local pivot = obj:GetPivot()
			local pos = pivot and pivot.Position or (obj.PrimaryPart and obj.PrimaryPart.Position)
			if pos then
				local dist = (pos - playerPos).Magnitude
				if dist < closestDist then
					closestDist = dist
					closest = { cframe = pivot or CFrame.new(pos) }
				end
			end
		end
	end
	return closest
end

local function getClosestMonster()
	local folder = Workspace:FindFirstChild("Monsters")
	if not folder or not rootPart then return nil end

	local playerPos = rootPart.Position
	local currentTime = tick()

	if autoBoss then
		local bossObj = nil
		local successMonsters, mChildren = pcall(function() return folder:GetChildren() end)

		if successMonsters and mChildren then
			for _, obj in pairs(mChildren) do
				if obj:IsA("Model") and not ignoredMonsters[obj] then
					local hum = obj:FindFirstChildOfClass("Humanoid")
					local hrp = obj:FindFirstChild("HumanoidRootPart") or obj.PrimaryPart

					if hum and hum.Health > 0 and hrp then
						local nameplate = hrp:FindFirstChild("Nameplate")
						local monsterText = ""
						if nameplate then
							local successLabels, labels = pcall(function() return nameplate:GetChildren() end)
							if successLabels and labels then
								for _, child in pairs(labels) do
									if child:IsA("TextLabel") and child:FindFirstChildOfClass("UIStroke") then
										monsterText = child.Text
										break
									end
								end
							end
						end
						if string.find(string.gsub(monsterText, "%s+", ""), "BoneDragon") then
							bossObj = obj
							break
						end
					end
				end
			end
		end

		if bossObj then
			if currentTarget ~= bossObj then
				currentTarget = bossObj
				targetAttackStartTime = currentTime
			end
			local pivot = bossObj:GetPivot()
			local pos = pivot and pivot.Position or bossObj.PrimaryPart.Position
			return { cframe = pivot or CFrame.new(pos) }
		else
			if not autoMonster then
				return { cframe = CFrame.new(monsterData["Bone Dragon"].pos + Vector3.new(0, 3, 0)) }
			end
		end
	end

	if currentTarget then
		local hum = currentTarget:FindFirstChildOfClass("Humanoid")
		local hrp = currentTarget:FindFirstChild("HumanoidRootPart") or currentTarget.PrimaryPart

		if not currentTarget.Parent or not hum or hum.Health <= 0 or not hrp then
			currentTarget = nil
		elseif currentTime - targetAttackStartTime >= 20 then
			ignoredMonsters[currentTarget] = true
			currentTarget = nil
		else
			local pivot = currentTarget:GetPivot()
			local pos = pivot and pivot.Position or hrp.Position
			if pos then return { cframe = pivot or CFrame.new(pos) } end
		end
	end

	if not autoMonster then return nil end

	local closest = nil
	local closestDist = math.huge
	local bestObj = nil

	local activeTargets = {}
	if selectedMonsters["⭐ Auto Level Match"] then
		local success, pLevel = pcall(function() return player.leaderstats.Level.Value end)
		if success and pLevel then
			local closestDiff = math.huge
			local bestMobName = nil
			for mName, data in pairs(monsterData) do
				if mName ~= "Bone Dragon" then
					local diff = math.abs(data.level - pLevel)
					if diff < closestDiff then
						closestDiff = diff
						bestMobName = mName
					end
				end
			end
			if bestMobName then
				activeTargets[bestMobName] = true
			end
		end
	else
		activeTargets = selectedMonsters
	end

	local successMonsters, mChildren = pcall(function() return folder:GetChildren() end)
	if not successMonsters or not mChildren then return nil end

	for _, obj in pairs(mChildren) do
		if obj:IsA("Model") and not ignoredMonsters[obj] then
			local hum = obj:FindFirstChildOfClass("Humanoid")
			local hrp = obj:FindFirstChild("HumanoidRootPart") or obj.PrimaryPart

			if hum and hum.Health > 0 and hrp then
				local nameplate = hrp:FindFirstChild("Nameplate")
				local monsterText = ""

				if nameplate then
					local successLabels, labels = pcall(function() return nameplate:GetChildren() end)
					if successLabels and labels then
						for _, child in pairs(labels) do
							if child:IsA("TextLabel") and child:FindFirstChildOfClass("UIStroke") then
								monsterText = child.Text
								break
							end
						end
					end
				end

				if monsterText ~= "" then
					local cleanMonsterText = string.gsub(monsterText, "%s+", "")
					local isSelectedMatch = false

					for name, isEnabled in pairs(activeTargets) do
						if name ~= "⭐ Auto Level Match" and isEnabled then
							local cleanTargetName = string.gsub(name, "%s+", "")
							if string.find(cleanMonsterText, cleanTargetName) or string.find(cleanTargetName, cleanMonsterText) then
								isSelectedMatch = true
								break
							end
						end
					end

					if isSelectedMatch then
						local pivot = obj:GetPivot()
						local pos = pivot and pivot.Position or hrp.Position
						if pos then
							local dist = (pos - playerPos).Magnitude
							if dist < closestDist then
								closestDist = dist
								closest = { cframe = pivot or CFrame.new(pos) }
								bestObj = obj
							end
						end
					end
				end
			end
		end
	end

	if bestObj then
		if currentTarget ~= bestObj then
			currentTarget = bestObj
			targetAttackStartTime = currentTime
		end
	else
		local activeZones = {}
		for name, isEnabled in pairs(activeTargets) do
			if name ~= "⭐ Auto Level Match" and isEnabled and monsterData[name] then
				table.insert(activeZones, monsterData[name].pos)
			end
		end

		if #activeZones > 0 then
			zoneIndex = ((zoneIndex - 1) % #activeZones) + 1
			local targetPos = activeZones[zoneIndex]
			return { cframe = CFrame.new(targetPos + Vector3.new(0, 3, 0)) }
		end
	end

	return closest
end

task.spawn(function()
	while true do
		task.wait(60)
		ignoredMonsters = {}
	end
end)

function startTreeFarm()
	task.spawn(function()
		while autoTree do
			local target = getClosestTree()
			if target and rootPart and rootPart.Parent then
				moveToTarget(target.cframe * CFrame.new(0, -2, 0))
			end
			task.wait(treeInterval)
		end
		removeVisualPath()
	end)
end

function startMonsterFarm()
	task.spawn(function()
		while autoMonster or autoBoss do
			local target = getClosestMonster()
			if target and rootPart and rootPart.Parent then
				local clusterPos = getDenseMonsterClusterPosition()
				if clusterPos then
					moveToTarget(CFrame.new(clusterPos + Vector3.new(0, 6, 0)))
				else
					moveToTarget(target.cframe * CFrame.new(0, 6, 0))
				end
			end
			task.wait(monsterInterval)
		end
		removeVisualPath()
	end)
end

local function getClosestFishingSpotCoord()
	if not rootPart then return fishingSpotCoords[1] end
	local playerPos = rootPart.Position
	local closestPos = fishingSpotCoords[1]
	local minDst = math.huge

	for _, pos in ipairs(fishingSpotCoords) do
		local dst = (pos - playerPos).Magnitude
		if dst < minDst then
			minDst = dst
			closestPos = pos
		end
	end
	return closestPos
end

local function triggerClosestFishingPrompt()
	local folder = Workspace:FindFirstChild("FishingSpots")
	if not folder or not rootPart then return end

	local playerPos = rootPart.Position
	local closestChild = nil
	local minDst = math.huge

	for _, child in ipairs(folder:GetChildren()) do
		local pos = nil
		if child:IsA("Model") then
			pos = child:GetPivot().Position
		elseif child:IsA("BasePart") then
			pos = child.Position
		end

		if pos then
			local dst = (pos - playerPos).Magnitude
			if dst < minDst then
				minDst = dst
				closestChild = child
			end
		end
	end

	if closestChild then
		local prompt = closestChild:FindFirstChild("FishingPrompt", true) or closestChild:FindFirstChildOfClass("ProximityPrompt", true)
		if prompt and prompt:IsA("ProximityPrompt") then
			if fireproximityprompt then
				fireproximityprompt(prompt)
			elseif typeof(prompt.InputHoldBegin) == "function" then
				prompt:InputHoldBegin()
				task.wait(prompt.HoldDuration or 0.1)
				prompt:InputHoldEnd()
			end
		end
	end
end

function startFishingSpotClaim()
	task.spawn(function()
		while autoFishingSpot do
			if rootPart and rootPart.Parent then
				local targetPos = getClosestFishingSpotCoord()
				moveToTarget(CFrame.new(targetPos))

				if autoFishingSpot then
					triggerClosestFishingPrompt()
				end
			end
			task.wait(3.0)
		end
		removeVisualPath()
	end)
end

local FISHING_TARGET_COLOR = Color3.fromRGB(255, 196, 87)
local FISHING_COLOR_TOLERANCE = 3
local FISHING_MIN_OVERLAP_RATIO = 0.4
local isFishingTouching = false

local function isFishingTargetColor(color)
	if not color then return false end
	local r = math.floor(color.R * 255 + 0.5)
	local g = math.floor(color.G * 255 + 0.5)
	local b = math.floor(color.B * 255 + 0.5)

	return math.abs(r - FISHING_TARGET_COLOR.R * 255) <= FISHING_COLOR_TOLERANCE and
	       math.abs(g - FISHING_TARGET_COLOR.G * 255) <= FISHING_COLOR_TOLERANCE and
	       math.abs(b - FISHING_TARGET_COLOR.B * 255) <= FISHING_COLOR_TOLERANCE
end

local function getFishingOverlapRatio(gui1, gui2)
	if not gui1.Visible or not gui2.Visible then return 0 end

	local pos1, size1 = gui1.AbsolutePosition, gui1.AbsoluteSize
	local pos2, size2 = gui2.AbsolutePosition, gui2.AbsoluteSize

	local overlapX = math.max(0, math.min(pos1.X + size1.X, pos2.X + size2.X) - math.max(pos1.X, pos2.X))
	local overlapY = math.max(0, math.min(pos1.Y + size1.Y, pos2.Y + size2.Y) - math.max(pos1.Y, pos2.Y))

	if overlapX <= 0 or overlapY <= 0 then return 0 end

	local overlapArea = overlapX * overlapY
	local smallerArea = math.min(size1.X * size1.Y, size2.X * size2.Y)
	if smallerArea <= 0 then return 0 end

	return overlapArea / smallerArea
end

local function pressFishingEKey()
	VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.E, false, game)
	task.wait(0.02)
	VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.E, false, game)
end

RunService.RenderStepped:Connect(function()
	if not autoFishing then 
		isFishingTouching = false
		return 
	end

	local hudGui = playerGui:FindFirstChild("HudGui")
	if not hudGui then 
		isFishingTouching = false
		return 
	end

	local fishingPanel = hudGui:FindFirstChild("FishingPanel")
	if not fishingPanel or not fishingPanel.Visible then 
		isFishingTouching = false
		return 
	end

	local segments = fishingPanel:FindFirstChild("Segments")
	local pointer = fishingPanel:FindFirstChild("Pointer")
	if not segments or not pointer then 
		isFishingTouching = false
		return 
	end

	local isRatioMet = false

	for _, segment in ipairs(segments:GetChildren()) do
		if segment:IsA("GuiObject") and segment.Visible then
			local segColor = segment:IsA("ImageLabel") and segment.ImageColor3 or segment.BackgroundColor3
			
			if isFishingTargetColor(segColor) then
				local ratio = getFishingOverlapRatio(segment, pointer)
				if ratio >= FISHING_MIN_OVERLAP_RATIO then
					isRatioMet = true
					break
				end
			end
		end
	end

	if isRatioMet then
		if not isFishingTouching then
			isFishingTouching = true
			pressFishingEKey()
		end
	else
		isFishingTouching = false
	end
end)

task.spawn(function()
	while true do
		if loopSpeedEnabled and humanoid and humanoid.Parent then
			pcall(function()
				if humanoid.WalkSpeed ~= customWalkSpeed then
					humanoid.WalkSpeed = customWalkSpeed
				end
			end)
		end
		task.wait(0.1)
	end
end)

task.spawn(function()
	while true do
		if antiAfk and humanoid and humanoid.Parent then
			pcall(function()
				VirtualUser:CaptureController()
				VirtualUser:ClickButton2(Vector2.new())
			end)
			if humanoid:GetState() ~= Enum.HumanoidStateType.Freefall then
				humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
			end
		end
		task.wait(25)
	end
end)

task.spawn(function()
	while true do
		if autoHeal and humanoid and humanoid.Parent then
			if humanoid.Health > 0 and humanoid.Health < (humanoid.MaxHealth * 0.2) then
				pcall(function()
					VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.R, false, game)
					task.wait(0.05)
					VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.R, false, game)
				end)
			end
		end
		task.wait(0.25)
	end
end)

task.spawn(function()
	while true do
		if autoDurability then
			pcall(function()
				local hudGui = playerGui:FindFirstChild("HudGui")
				local statPanel = hudGui and hudGui:FindFirstChild("StatPanel")
				local bottomRow = statPanel and statPanel:FindFirstChild("BottomRow")
				local chip = bottomRow and bottomRow:FindFirstChild("DurabilityChip")

				if chip and chip:IsA("TextLabel") then
					local n = tonumber(chip.Text:match("(%d+)"))
					if n and n <= 50 then
						VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.V, false, game)
						task.wait(0.05)
						VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.V, false, game)
					end
				end
			end)
		end
		task.wait(0.5)
	end
end)

task.spawn(function()
	while true do
		if autoAttack then
			pcall(function()
				VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
				task.wait(0.05)
				VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.F, false, game)
			end)
		end
		task.wait(0.15)
	end
end)

task.spawn(function()
	while true do
		if autoMagic then
			local now = tick()
			for i = 1, 4 do
				if selectedSkills[i] and (now - lastSkillFire[i] >= skillCooldowns[i]) then
					local keyCode = skillKeyCodes[i]
					pcall(function()
						VirtualInputManager:SendKeyEvent(true, keyCode, false, game)
						task.wait(0.04)
						VirtualInputManager:SendKeyEvent(false, keyCode, false, game)
					end)
					lastSkillFire[i] = now
				end
			end
		end
		task.wait(0.05)
	end
end)

local function setupCharacter(newChar)
	character = newChar
	humanoid = newChar:WaitForChild("Humanoid")
	rootPart = newChar:WaitForChild("HumanoidRootPart")

	isJustRespawned = true
	isFlying = false
	currentTarget = nil

	if not loopSpeedEnabled then customWalkSpeed = humanoid.WalkSpeed end

	task.spawn(function()
		local head = newChar:WaitForChild("Head", 5)
		if head then
			local nameplate = head:FindFirstChild("Nameplate")
			if nameplate then
				local userLabel = nameplate:FindFirstChild("UserLabel")
				if userLabel then userLabel:Destroy() end
				local nameLabel = nameplate:FindFirstChild("NameLabel")
				if nameLabel then nameLabel:Destroy() end
			end
		end
	end)

	humanoid.Died:Connect(function()
		removeVisualPath()
		isFlying = false
		currentTarget = nil
	end)
end

player.CharacterAdded:Connect(setupCharacter)
if character then setupCharacter(character) end
