# test627
# 匯入 OpenAI 函式庫
import openai

# 你的 API 金鑰，從 https://platform.openai.com/account/api-keys 拿
openai.api_key = ""

# 想要問 AI 的內容
prompt = "請幫我寫一段python程式入門的關鍵"

# 呼叫 OpenAI 的 ChatGPT 模型
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",  # 如果你有 GPT-4，可以改成 "gpt-4"
    messages=[
        {"role": "system", "content": "你是一個親切又鼓勵人的助手"},
        {"role": "user", "content": prompt}
    ]
)

# 把回覆的內容取出來
answer = response['choices'][0]['message']['content']

# 印出 AI 的回覆
print("AI 回覆：\n", answer)

# 把回覆寫入檔案
with open("ai_response.txt", "w", encoding="utf-8") as f:
    f.write(answer)
