# Python_robat_telegram
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters

TOKEN = "PUT_YOUR_BOT_TOKEN_HERE"

def start(update, context):
    update.message.reply_text("سلام 👋\nربات با موفقیت روشن شد!")

def help_command(update, context):
    update.message.reply_text("دستورات:\n/start\n/help")

def echo(update, context):
    text = update.message.text
    update.message.reply_text(f"تو گفتی: {text}")

def main():
    updater = Updater(TOKEN, use_context=True)
    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(CommandHandler("help", help_command))
    dp.add_handler(MessageHandler(Filters.text & ~Filters.command, echo))

    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()