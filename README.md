Saiga Mistral 7B - Генерация шуток на русском
Ноутбук для запуска русскоязычной модели Saiga Mistral 7B с квантизацией 4-bit для экономии памяти. Пример генерации шуток.

🚀 Быстрый старт
Установка
bash
pip install torch transformers datasets accelerate evaluate bitsandbytes trl peft
Авторизация на Hugging Face
python
from huggingface_hub import login
login()  # или передайте токен
📦 Используемые модели
Модель: IlyaGusev/saiga_mistral_7b

Токенизатор: Тот же, что и модель

Квантизация: 4-bit (NF4) через BitsAndBytes

🔧 Настройки квантизации
python
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_use_double_quant=True,
)
💬 Класс Conversation
Управляет диалогом и форматирует промпты в нужном формате:

Системный промпт

Сообщения пользователя

Ответы бота

Шаблоны сообщений

🎯 Пример использования
python
# Создание запроса
joke = 'Расскажи 3 смешные шутки'

# Формирование диалога
conversation = Conversation()
conversation.add_user_message(joke)
prompt = conversation.get_prompt(tokenizer)

# Генерация ответа
output = generate(model, tokenizer, prompt, generation_config)
print(output)
📊 Требования к памяти
Модель в 4-bit занимает ~4-5 GB VRAM

Подходит для запуска на Google Colab (T4 GPU)

🌟 Особенности
Русскоязычная модель

Оптимизация памяти через 4-bit квантизацию

Готовый класс для управления диалогом

Пример генерации текста

