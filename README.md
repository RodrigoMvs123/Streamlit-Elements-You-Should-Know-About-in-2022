# Streamlit-Elements-You-Should-Know-About-in-2022

https://www.youtube.com/watch?v=_Um12_OlGgw
##

https://streamlit.io/

##

https://share.streamlit.io/

##
Streamlit.py 
import Streamlit as st
import time 

if "photo" not in st.session_state:
    st.session_state["photo"]="not done"

col1, col2, col3 = st.columns([1,2,1])

col1.markdown(" # Welcome to my app! ")
col1.markdown("Here is some info on the app. ") 


def change_photo_state ():
     st.session_state["photo"]="done"


uploaded_photo = col2.file_uploader("Upload a photo", on change=change_photo_state)
camera_photo = col2.camera_input("Take a photo", on change=change_photo_state)
 
if  st.session_state["photo"] == "done":    
    progress_bar = col2.progress(0)

    for perc_completed in range(100):
        time.sleep(0.05)
        progress_bar.progress(perc_completed+1)

    col2.success("Photo uploaded successfully!")

    col3.metric(label="Temperature", value="60 °C", delta="3 °C")

    with st.expander("Click to read more"):
        st.write("Helo, here are more details on this topic that you were interested in.")
        
        if uploaded_photo is None:
            st.image(camera_photo)
        else:
            st.image(uploaded_photo)


