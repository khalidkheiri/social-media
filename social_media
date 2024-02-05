import streamlit as st
import requests
from bs4 import BeautifulSoup
from deep_translator import GoogleTranslator


st.set_page_config(
    page_title="Khalid Kheiri")

st.title("Social Media News")

page = requests.get("https://www.socialmediatoday.com/")

soup = BeautifulSoup(page.content)

rows = soup.find_all("li", class_="row feed__item")

titles = []
descs = []
imgs = []
for index, row in enumerate(rows):
    titles.append(row.find("a", class_=f"analytics t-dash-feed-item-{index+1}").text)
    descs.append(row.find("p", class_="feed__description").text)
    imgs.append("https://www.socialmediatoday.com"+row.find("img", class_="")["src"])


for i in range(len(rows)):
    title = titles[i].strip().capitalize()
    translated1 = GoogleTranslator(source='auto', target='ar').translate(title)

    desc = descs[i].strip().capitalize()
    translated2 = GoogleTranslator(source='auto', target='ar').translate(desc)

    col1, col2 = st.columns((1, 1), gap="large")
    col1.image(imgs[i])
    col2.markdown(f"<h3 style='color:Tomato;direction: RTL;'>{translated1}</h3>", unsafe_allow_html=True)
    col2.markdown(f"<h5 style='color:DodgerBlue;direction: RTL;'>{translated2}</h5>", unsafe_allow_html=True)
    st.markdown("---")
