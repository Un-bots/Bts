# A Powerful Music And Management Bot
# Property Of Un Indian Largest Support Group
# Rocks © @UN_BOTS © UNKNOWN 
# Owner UNKNOWN + UN_BOTS + UN_W0RLD 


import os, logging, asyncio
from telethon import Button
from telethon import TelegramClient, events
from telethon.tl.types import ChannelParticipantAdmin
from telethon.tl.types import ChannelParticipantCreator
from telethon.tl.types import ChannelParticipantsAdmins
from telethon.tl.functions.channels import GetParticipantRequest
from telethon.errors import UserNotParticipantError
from pyrogram import Client, filters
from pyrogram.types import Message, InlineKeyboardMarkup, InlineKeyboardButton


logging.basicConfig(
    level=logging.INFO, format="%(name)s - [%(levelname)s] - %(message)s"
)
LOGGER = logging.getLogger(__name__)

api_id = int(os.environ.get("APP_ID", ""))
api_hash = os.environ.get("API_HASH", "")
bot_token = os.environ.get("BOT_TOKEN", "")
client = TelegramClient("client", api_id, api_hash).start(bot_token=bot_token)
spam_chats = []




@client.on(events.NewMessage(pattern="^/mentionall ?(.*)"))
async def mentionall(event):
    chat_id = event.chat_id
    if event.is_private:
        return await event.respond(
            "ᴛʜɪs ᴄᴏᴍᴍᴀɴᴅ ᴄᴀɴ ʙᴇ ᴜsᴇ ɪɴ ɢʀᴏᴜᴘs ᴀɴᴅ ᴄʜᴀɴɴᴇʟs"
        )

    is_admin = False
    try:
        partici_ = await client(GetParticipantRequest(event.chat_id, event.sender_id))
    except UserNotParticipantError:
        is_admin = False
    else:
        if isinstance(
            partici_.participant, (ChannelParticipantAdmin, ChannelParticipantCreator)
        ):
            is_admin = True
    if not is_admin:
        return await event.respond("ᴏɴʟʏ ᴀᴅᴍɪɴs ᴄᴀɴ ᴍᴇɴᴛɪᴏɴ ᴀʟʟ")

    if event.pattern_match.group(1) and event.is_reply:
        return await event.respond("ɢɪᴠᴇ ᴍᴇ ᴏɴᴇ ᴀʀɢᴜᴍᴇɴᴛ")
    elif event.pattern_match.group(1):
        mode = "text_on_cmd"
        msg = event.pattern_match.group(1)
    elif event.is_reply:
        mode = "text_on_reply"
        msg = await event.get_reply_message()
        if msg == None:
            return await event.respond(
                "ɪ ᴄᴀɴ'ᴛ ᴍᴇɴᴛɪᴏɴ ᴍᴇᴍʙᴇʀs ꜰᴏʀ ᴏʟᴅᴇʀ ᴍᴇssᴀɢᴇs! (ᴍᴇssᴀɢᴇs ᴡʜɪᴄʜ ᴀʀᴇ sᴇɴᴛ ʙᴇꜰᴏʀᴇ ɪ'ᴍ ᴀᴅᴅᴇᴅ ᴛᴏ ɢʀᴏᴜᴘ)"
            )
    else:
        return await event.respond(
            "ʀᴇᴘʟʏ ᴛᴏ ᴀ ᴍᴇssᴀɢᴇ ᴏʀ ɢɪᴠᴇ ᴍᴇ sᴏᴍᴇ ᴛᴇxᴛ ᴛᴏ ᴍᴇɴᴛɪᴏɴ ᴏᴛʜᴇʀs"
        )

    spam_chats.append(chat_id)
    usrnum = 0
    usrtxt = ""
    async for usr in client.iter_participants(chat_id):
        if not chat_id in spam_chats:
            break
        usrnum += 1
        usrtxt += f"[{usr.first_name}](tg://user?id={usr.id}) "
        if usrnum == 5:
            if mode == "text_on_cmd":
                txt = f"{usrtxt}\n\n{msg}"
                await client.send_message(chat_id, txt)
            elif mode == "text_on_reply":
                await msg.reply(usrtxt)
            await asyncio.sleep(2)
            usrnum = 0
            usrtxt = ""
    try:
        spam_chats.remove(chat_id)
    except:
        pass


@client.on(events.NewMessage(pattern="^/admins|/admin|@admin|@admins ?(.*)"))
async def _(event):
    chat_id = event.chat_id
    if event.is_private:
        return await event.respond("sᴏʀʀʏ ʏᴏᴜ ᴄᴀɴ ᴍᴇɴᴛɪᴏɴ ᴀᴅᴍɪɴ ᴏɴʟʏ ɪɴ ɢʀᴏᴜᴘ")

    is_admin = False
    try:
        partici_ = await client(GetParticipantRequest(event.chat_id, event.sender_id))
    except UserNotParticipantError:
        is_admin = False
    else:
        if isinstance(
            partici_.participant, (ChannelParticipantAdmin, ChannelParticipantCreator)
        ):
            is_admin = True
    if not is_admin:
        return await event.respond("ᴏɴʟʏ ᴀᴅᴍɪɴ ᴄᴀɴ ᴍᴇɴᴛɪᴏɴ ɢʀᴏᴜᴘ ᴀᴅᴍɪɴs")

    if event.pattern_match.group(1) and event.is_reply:
        return await event.respond("ɢɪᴠᴇ sᴏᴍᴇ ᴛᴇxᴛ ᴛᴏ ᴍᴇɴᴛɪᴏɴ")
    elif event.pattern_match.group(1):
        mode = "text_on_cmd"
        msg = event.pattern_match.group(1)
    elif event.is_reply:
        mode = "text_on_reply"
        msg = await event.get_reply_message()
        if msg == None:
            return await event.respond(
                "ɪ ᴄᴀɴ'ᴛ ᴍᴇɴᴛɪᴏɴ ᴍᴇᴍʙᴇʀs ꜰᴏʀ ᴏʟᴅᴇʀ ᴍᴇssᴀɢᴇs! (ᴍᴇssᴀɢᴇs ᴡʜɪᴄʜ ᴀʀᴇ sᴇɴᴛ ʙᴇꜰᴏʀᴇ ɪ'ᴍ ᴀᴅᴅᴇᴅ ᴛᴏ ɢʀᴏᴜᴘ)"
            )
    else:
        return await event.respond(
            "ʀᴇᴘʟʏ ᴛᴏ ᴀ ᴍᴇssᴀɢᴇ ᴏʀ ɢɪᴠᴇ ᴍᴇ sᴏᴍᴇ ᴛᴇxᴛ ᴛᴏ ᴍᴇɴᴛɪᴏɴ ᴏᴛʜᴇʀs!"
        )

    spam_chats.append(chat_id)
    usrnum = 0
    usrtxt = ""
    chat = await event.get_input_chat()
    async for x in client.iter_participants(chat, filter=ChannelParticipantsAdmins):
        if not chat_id in spam_chats:
            break
        usrnum += 1
        usrtxt += f" \n [{x.first_name}](tg://user?id={x.id})"
        if usrnum == 5:
            if mode == "text_on_cmd":
                txt = f"{usrtxt}\n\n{msg}"
                await client.send_message(chat_id, txt)
            elif mode == "text_on_reply":
                await msg.reply(usrtxt)
            await asyncio.sleep(2)
            usrnum = 0
            usrtxt = ""
    try:
        spam_chats.remove(chat_id)
    except:
        pass


@client.on(events.NewMessage(pattern="^/cancel$"))
async def cancel_spam(event):
    if not event.chat_id in spam_chats:
        return await event.respond("ᴛʜᴇʀᴇ ɪs ɴᴏ ᴘʀᴏᴄᴄᴇss ᴏɴ ɢᴏɪɴɢ...")
    else:
        try:
            spam_chats.remove(event.chat_id)
        except:
            pass
        return await event.respond("sᴛᴏᴘᴘᴇᴅ.")


print(">> ᴜɴ ᴍᴇɴᴛɪᴏɴ BOT WORKING <<")
client.run_until_disconnected()
