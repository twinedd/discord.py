import discord, time, openai, random, requests
import словать as s
from bs4 import BeautifulSoup
from discord.ext import commands
token = '' #ваш токен дискорда сюда
openai.api_key = "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"
bot = commands.Bot(command_prefix = '.', self_bot = True)
print("v2")

@bot.command()
async def помощь(ctx):
    print("")
    await ctx.reply("```!кубик -- Генерирует случайное число, от 1 до 6\n!спам -- спамит сообщениями, первый арг это сколько итераций, второй арг - это сообщение\n!спам2 -- это второй вид спама\n!ранпредложение -- принимает аргументы 'ру' и 'англ\n' ```")

@bot.command()
async def кубик(ctx):
        numran = random.randint(1, 6)
        await ctx.send(f"```Выпало число >>> {numran}```")

@bot.command()
async def спам(ctx, iteration, *, text):
    for i in range(int(iteration)):
        await ctx.reply(f'```{text}```')

@bot.command()
async def спам2(ctx, iteration, *, text):
    for i in range(int(iteration)):
        await ctx.send(f'```{text}```')

#@commands.cooldown(rate=1, per=5, type=commands.BucketType.user)
@bot.command()
async def ранпредложение(ctx, lang):
    if lang == 'ру':
        g = len(s.coolWords) - 1
        pred = []
        for i in range(random.randint(2, 20)):
            word = s.coolWords[random.randint(0, g)]
            pred.append(word)
            output1 = " ".join(pred)
        await ctx.reply(f'```{output1}```')
        pred = []
    elif lang == 'англ':
        ga = len(s.coolWordsENG) - 1
        predENG = []
        for i in range(random.randint(2, 20)):
            worda = s.coolWordsENG[random.randint(0, ga)]
            predENG.append(worda)
            output = " ".join(predENG)
        await ctx.reply(f'```{output}```')
        predENG = []

@bot.command()
async def гпинг(ctx, user_id):
    await ctx.message.delete()
    await ctx.send('||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||​||||||||||||<@' + str(user_id) + ">")
@bot.command()
async def гпинг2(ctx, user_id):
    await ctx.message.delete()
    await ctx.send("<@" + str(user_id) + ">", delete_after = 0.01)

#@commands.cooldown(rate=1, per=5, type=commands.BucketType.user)
@bot.command()
async def самолетик(ctx):
    await ctx.message.delete()
    animation = ['.      :airplane:', '.    :airplane:',  '.  :airplane:', '.:airplane:']
    msg = await ctx.send('.           :airplane:')
    for i in animation:
        await msg.edit(content=i)
        time.sleep(.5)

        

@bot.command()
async def чатгпт(ctx, *, promt2):
    print("Loading...")
    await ctx.reply('Текст генерируется...', delete_after = 1)
    model_engine = "text-davinci-003"
    completion = openai.Completion.create(
        prompt = promt2,
        engine=model_engine,
        temperature=0.5,
        top_p=1,
        frequency_penalty=0,
        presence_penalty=0.0,
        max_tokens = 1024
    )
    await ctx.reply(f'```{completion.choices[0].text}```')


@bot.command()
async def аватар(ctx, userID: discord.User):
    await ctx.reply(str(userID.avatar_url))

@bot.command()
async def найди(ctx,*,search):
    s=requests.get(f'https://www.google.com/search?q={search}&hl=en&tbm=isch&sxsrf=APwXEdeSDXkW6cshlUSrlZktTpWKEbKi8Q%3A1680718978108&source=hp&biw=1280&bih=899&ei=grwtZNGSApCGxc8PxaSNgA8&iflsig=AOEireoAAAAAZC3KklNBlCtaKkuwgJ0AzvsySJAv5C7l&ved=0ahUKEwjR25yNrpP-AhUQQ_EDHUVSA_AQ4dUDCAY&uact=5&oq=hello&gs_lcp=CgNpbWcQAzIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQ6BwgjEOoCECc6BAgjECdQjQRYzQhgyQpoAXAAeACAAWKIAcYDkgEBNZgBAKABAaoBC2d3cy13aXotaW1nsAEK&sclient=img').text
    q=BeautifulSoup(s,'lxml')
    grab=q.findAll('img')[random.randint(1,15)].get('src')
    await ctx.channel.send(content=f'поиск по запросу | {search}{grab}')
bot.run(token, bot=False)
