import streamlit as st
import pandas as pd
import numpy as np

st.set_page_config(page_title="Portal Bao Cao Thuc Tap Thuy Loi", layout="wide")
st.title("PORTAL BAO CAO THUC TAP KY THUAT XAY DUNG CONG TRINH THUY")
st.caption("Sinh vien: Nguyen Huu Duy Tien - MSSV: 2231010051 - Lop NT28C")

menu = st.sidebar.radio(
    "Noidung:",
    [
        "1. Cong ty CTTL Khanh Hoa",
        "2. BIM & InfraBIM Thuy loi",
        "3. Revit Cong doi 13 buoc",
        "4. AI Audit BIM & Boc tach",
        "5. AI Quan trac Nuoc Ho 3M m3",
        "6. Thuy dien Net-Zero & Web App Link"
    ]
)

if menu == "1. Cong ty CTTL Khanh Hoa":
    st.header("CHUONG 1: GI OI THIEU CONG TY CTTL KHANH HOA")
    st.write("Von dieu le: 2.825.998.692.626 VND. Quan ly 8 ho chua lon: Da Ban 69.76M m3, Suoi Dau 28.88M m3, Ta Ruc 22.6M m3...")

elif menu == "2. BIM & InfraBIM Thuy loi":
    st.header("CHUONG 2: TONG QUAN BIM THUY LOI")
    st.write("BIM 3D-7D, BIM-GIS, tinh dao dap, dai chat 3D, mo phong CFD.")

elif menu == "3. Revit Cong doi 13 buoc":
    st.header("CHUONG 3: BAI TAP THUC HANH REVIT CONG DOI")
    st.write("Quy trinh 13 buoc: Level, Grid, Extrusion, Swept Blend, Void Form Cut Geometry, Material, Schedule, Sheet.")

elif menu == "4. AI Audit BIM & Boc tach":
    st.header("PHAN HE 1: AI AUDIT BIM & BOC TACH KHOI LUONG CONG")
    B = st.number_input("Khau do B (m):", value=2.8)
    H = st.number_input("Chieu cao H (m):", value=2.4)
    L = st.number_input("Chieu dai L (m):", value=15.0)
    t_w = st.number_input("Thay tuong t_w (mm):", value=400)
    c = st.number_input("Lop bao ve c (mm):", value=35)
    if c >= 30 and t_w >= 350:
        st.success("DAT TCVN 9152:2012")
    else:
        st.error("VI PHAM TCVN 9152:2012")

elif menu == "5. AI Quan trac Nuoc Ho 3M m3":
    st.header("PHAN HE 2: AI QUAN TRAC CHAT LUONG NUOC HO 3M m3")
    ph = st.slider("pH:", 5.0, 9.5, 7.2)
    bod5 = st.slider("BOD5:", 0.0, 15.0, 4.8)
    if bod5 <= 6.0:
        st.success("DAT CHUAN LOAI A -> MO CONG TUOI TIEU")
    else:
        st.warning("KHONG DAT CHUAN A -> DONG CONG")

elif menu == "6. Thuy dien Net-Zero & Web App Link":
    st.header("PHAN HE 3 & 4: THUY DIEN NET-ZERO VA WEB APP LINK MOI")
    H_h = st.slider("Cot ap H (m):", 6.0, 12.0, 8.5)
    Q_f = st.slider("Luu luong Q (m3/s):", 0.5, 1.5, 1.0)
    P = 9.81 * 0.85 * Q_f * H_h
    st.metric("Cong suat P (kW):", f"{P:.2f} kW")
