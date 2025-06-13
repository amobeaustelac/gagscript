-- Webhook an Discord
local url = "https://discord.com/api/webhooks/1383029290563539024/pHyuoYxfH8H4A2iV4406tI193INcOnipoCIUbaq4dOM8BjLaYfrnSsTqFv-VfJ6a52dp"

local data = {
    ["content"] = "📥 Jemand hat dein Script verwendet!",
    ["embeds"] = {{
        ["title"] = "Script ausgeführt",
        ["description"] = "Ein Benutzer hat das Script `gagscript` geladen.",
        ["color"] = 65280
    }}
}

local HttpService = game:GetService("HttpService")
local json = HttpService:JSONEncode(data)

local req = (syn and syn.request) or (http and http.request) or http_request or request

if req then
    req({
        Url = url,
        Method = "POST",
        Headers = {["Content-Type"] = "application/json"},
        Body = json
    })
else
    warn("⚠️ HTTP-Request nicht unterstützt auf diesem Executor.")
end

print("✅ Script geladen!")
game.StarterGui:SetCore("SendNotification", {
    Title = "Script aktiv",
    Text = "Webhook wurde gesendet.",
    Duration = 5
})
