# dlcksdud.github.io
import tkinter as tk
from tkinter import messagebox

# [상수 정의] 변수 명세서: 기준 ZERO = 0
ZERO = 0

def process_logic():
    """순서도 및 처리과정을 수행하는 함수"""
    try:
        # 1.1 2개의 정수 입력받기 (right, left)
        right = int(entry_right.get())
        left = int(entry_left.get())
        
        # b = right - left (크기 판별)
        b = right - left
        
        # 1.2 두 정수 사이의 대소 판별 (b >= ZERO)
        if b >= ZERO:
            big = right
            small = left
        else:
            big = left
            small = right
            
        # 1.3 두 정수의 차이 구하기
        a = big - small
        
        # 1.4 결과 출력 (a, big)
        label_result_a.config(text=f"두 수의 차 (a): {a}")
        label_result_big.config(text=f"더 큰 정수 (big): {big}")
        
    except ValueError:
        messagebox.showerror("입력 오류", "right와 left에 올바른 정수를 입력해주세요.")

def reset_fields():
    """입력 칸 및 결과 초기화"""
    entry_right.delete(0, tk.END)
    entry_left.delete(0, tk.END)
    label_result_a.config(text="두 수의 차 (a): -")
    label_result_big.config(text="더 큰 정수 (big): -")

# --- GUI 창 설정 ---
root = tk.Tk()
root.title("두 수의 차 및 대소 비교 프로그램")
root.geometry("320 x 280")
root.resizable(False, False)

# 입력 영역
frame_input = tk.Frame(root, pady=10)
frame_input.pack()

tk.Label(frame_input, text="정수 1 (right):").grid(row=0, column=0, padx=5, pady=5, sticky="e")
entry_right = tk.Entry(frame_input, width=12)
entry_right.grid(row=0, column=1, padx=5, pady=5)

tk.Label(frame_input, text="정수 2 (left):").grid(row=1, column=0, padx=5, pady=5, sticky="e")
entry_left = tk.Entry(frame_input, width=12)
entry_left.grid(row=1, column=1, padx=5, pady=5)

# 실행 및 초기화 버튼
frame_button = tk.Frame(root)
frame_button.pack(pady=5)

btn_calc = tk.Button(frame_button, text="계산하기", command=process_logic, width=10, bg="#4CAF50", fg="white")
btn_calc.grid(row=0, column=0, padx=5)

btn_reset = tk.Button(frame_button, text="다시 입력", command=reset_fields, width=10)
btn_reset.grid(row=0, column=1, padx=5)

# 결과 출력 영역 (순서도의 출력 기호 위치)
frame_result = tk.LabelFrame(root, text=" 출력 결과 ", padx=10, pady=10)
frame_result.pack(pady=10, fill="x", padx=20)

label_result_big = tk.Label(frame_result, text="더 큰 정수 (big): -", font=("Arial", 10, "bold"))
label_result_big.pack(anchor="w", pady=2)

label_result_a = tk.Label(frame_result, text="두 수의 차 (a): -", font=("Arial", 10, "bold"))
label_result_a.pack(anchor="w", pady=2)

# GUI 실행 (순서도의 START -> 반복 -> STOP)
root.mainloop()
