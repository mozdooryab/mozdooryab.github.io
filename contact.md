---
layout: default
title: "ارتباط با ما"
permalink: /contact/
---

# ارتباط با ما

اگر سوال، پیشنهاد یا فایل برای ما دارید، از فرم زیر استفاده کنید.

<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST" enctype="multipart/form-data" style="display:grid;gap:16px;margin-top:24px;background:var(--surface);border:1px solid var(--border);border-radius:20px;padding:24px;">
  <input type="hidden" name="_subject" value="پیام جدید از صفحه تماس">
  <input type="hidden" name="page_url" value="/contact/">
  <input type="hidden" name="page_title" value="contact">

  <label>
    <div style="margin-bottom:8px;font-weight:700;">نام</div>
    <input name="name" type="text" required style="width:100%;padding:14px 16px;border:1px solid var(--border);border-radius:14px;background:var(--bg);color:var(--text);font:inherit;">
  </label>

  <label>
    <div style="margin-bottom:8px;font-weight:700;">ایمیل</div>
    <input name="email" type="email" required style="width:100%;padding:14px 16px;border:1px solid var(--border);border-radius:14px;background:var(--bg);color:var(--text);font:inherit;">
  </label>

  <label>
    <div style="margin-bottom:8px;font-weight:700;">پیام</div>
    <textarea name="message" rows="7" required style="width:100%;padding:14px 16px;border:1px solid var(--border);border-radius:14px;background:var(--bg);color:var(--text);font:inherit;"></textarea>
  </label>

  <label>
    <div style="margin-bottom:8px;font-weight:700;">فایل</div>
    <input name="attachment" type="file" style="width:100%;padding:10px;border:1px solid var(--border);border-radius:14px;background:var(--bg);color:var(--text);font:inherit;">
  </label>

  <button type="submit" style="border:none;border-radius:999px;padding:14px 18px;background:var(--primary);color:white;font:inherit;font-weight:800;cursor:pointer;">
    ارسال پیام
  </button>
</form>
