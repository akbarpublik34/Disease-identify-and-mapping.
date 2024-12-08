import streamlit as st
import requests #For making HTTP requests to the backend

st.title("Image Captioning App")

uploaded_file = st.file_uploader("Choose an image...", type=["jpg", "jpeg", "png"])

if uploaded_file is not None:
    st.image(uploaded_file, caption="Uploaded Image.", use_column_width=True)

    # ---  Send the image to your backend and get the caption ---
    try:
        files = {'image': uploaded_file.getvalue()}
        response = requests.post("http://your-backend-address:3000/caption", files=files)  # Replace with your backend URL
        response.raise_for_status()  # Raise HTTPError for bad responses (4xx or 5xx)
        data = response.json()
        caption = data["caption"]
        st.success(f"Caption: {caption}")

    except requests.exceptions.RequestException as e:
        st.error(f"Error communicating with the backend: {e}")
    except KeyError as e:
        st.error(f"Unexpected response from backend: Missing key {e}")
    except Exception as e:
        st.exception(e) #Shows more details, use carefully in production
