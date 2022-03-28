import discord #импорт библиотек
from discord.ext import commands

client = commands.Bot( command_prefix = ".") # префикс команды 

PREFIX = "."

#WORDS
hello_words = ["бот", "bot",]

@client.event

async def on_ready():
	print ("BOT CONNECTED")

@client.command( pass_context = True)

async def hello( ctx):
	await ctx.send("Hello. I am a BOT on discord")

@client.command(pass_context = True)

async def clear(ctx, amount = 100):
	await ctx.channel.purge(limit = amount)


@client.event 

async def on_message( message):
	msg = message.content.lower()

	if msg in hello_words:
		await message.channel.send("Привет, чтобы узнать команды напиши - .help")


		# Connect

	token = open("token.txt", "r").readline()

	client.run(token)
