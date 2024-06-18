# streamlit_test
A test repo to show a streamlit bug I encountered

# Explanation
This is what I posted to the [help forums with streamlit]([url](https://discuss.streamlit.io/t/10-items-in-popover-showing-above-button-on-laptop-but-not-monitor/72862)):

Hello all -

I’ve been using streamlit to build an internal company dashboard for about 6 months now and it has been great. I just ran into my first potential bug:

I have multipage app for which I made a custom menu using a combination of st.popover and page_link. I have found that if I have more than 9 items in my popover, it displays above the button on a laptop or tablet, but not when the same computer is plugged into an external monitor.

I’ve done some testing and created a simple reproduceable example below: In my reprex, I found that I can have many items in my popover without trouble. But adding in a logo creates the problem on my laptop (but not on my monitor) when I get to 11 items.
<img width="389" alt="Screenshot 2024-06-18 at 12 53 35 PM" src="https://github.com/mhollander/streamlit_test/assets/1609252/94283e92-e470-4a23-929b-6a6039b938d2">

<img width="378" alt="Screenshot 2024-06-18 at 12 53 28 PM" src="https://github.com/mhollander/streamlit_test/assets/1609252/b3d744ad-4332-4072-af67-958b2e6bc9af">



The expected behavior is that the container stays below the button, but has a scrollbar like on my monitor. See image of the same popover working fine on my external monitor:
![Screenshot 2024-06-18 at 12 53 11 PM](https://github.com/mhollander/streamlit_test/assets/1609252/32700d74-a322-473c-a524-8ea7597369c5)


The positioning of the container (above the button) makes it impossible to use.
Does anyone know why this happens and how to prevent it from happening? I definitely want to have more than 9 items in my menu!

It appears that this has to do with vertical screen real estate. I can reproduce the laptop monitor problem by just zooming in a few times on my external monitor.

Below is a reprex, which is also a part of this repo.

Thank you for your help!
Mike

import streamlit as st

with st.sidebar:
    st.image("assets/heights-logo-tiny.png")
    menu = st.popover("Menu")
    menu.markdown("###### Line1")
    menu.markdown("###### Line2")
    menu.markdown("###### Line3")
    menu.markdown("###### Line4")
    menu.markdown("###### Line5")
    menu.markdown("###### Line6")
    menu.markdown("###### Line7")
    menu.markdown("###### Line8")
    menu.markdown("###### Line9")
    menu.markdown("###### Line10")
    menu.markdown("###### Line11")
    menu.markdown("###### Line12")
    
    menu2 = st.popover("Menu")
    menu2.markdown("###### Line1")
    menu2.markdown("###### Line2")
    menu2.markdown("###### Line3")
    menu2.markdown("###### Line4")
    menu2.markdown("###### Line5")
    menu2.markdown("###### Line6")
    menu2.markdown("###### Line7")
    menu2.markdown("###### Line8")
    menu2.markdown("###### Line9")
Version info: streamlit 1.35, python 3.11
