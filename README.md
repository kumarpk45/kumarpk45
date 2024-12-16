for chat_id in DAILY_POST_UPDATE:
                            if movie_docs:
                                img_url = movie_docs[0].get("img_url", None)
                                if img_url:
                                    try:
                                        await User.send_photo(
                                            chat_id=chat_id,
                                            photo=img_url,
                                            caption=text,
                                        )
                                    except Exception as e:
                                        logging.error(f"Error sending photo: {e}")
                                        await User.send_message(
                                            chat_id=chat_id,
                                            text=text,
                                            disable_web_page_preview=True,
                                        )
                                else:
                                    await User.send_message(
                                        chat_id=chat_id,
                                        text=text,
                                        disable_web_page_preview=True,
                                    )
                            else:
                                await User.send_message(
                                    chat_id=chat_id,
                                    text=text,
                                    disable_web_page_preview=True,
                                )
