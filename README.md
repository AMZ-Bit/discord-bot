# discord-bot
Sexbot

import os
import discord
import requests 
import json 


client = discord.Client() 

def get_quote():
  response = requests.get("https://zenquotes.io/api/random")
  json_data = json.loads(response.text)
  quote = json_data[0]["q"]+ " -" + json_data[0]["a"]
  return(quote) 



@client.event  
async def on_ready(): 
   print("We have logged in as {0.user}".format(client))

@client.event     
async def on_message(message):
  if message.author == client.user:
    return  

  if message.content.startswith("$hola"):
    await message.channel.send("SEXOO!!")
  if message.content.startswith("$jhon"): 
    await message.channel.send("Jhon Esteban Alias: Jhon Embuste")
  if message.content.startswith("$nando"):
    await message.channel.send("Nando Garcia Alias: Nando Plata")
  if message.content.startswith("$nikol"):
    await  message.channel.send("Nikol Baute Alias: Nikol Audifonos")
  if message.content.startswith("$commands"):
    await message.channel.send("$hola \n $jhon \n $nando \n $nikol \n $commands \n $clase \n $papa \n $frase ")
  if message.content.startswith("$clase"):
    await message.channel.send("Clase de ingles Nikol https://us06web.zoom.us/j/4507340023") 
  if message.content.startswith("$papa"):
    await message.channel.send("Mi Papa Se Llama Edgar")
  if message.content.startswith("$frase"):
    quote =  get_quote()
    await message.channel.send(quote)

client.run(os.environ['TOKEN'])
