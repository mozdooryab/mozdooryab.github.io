---
layout: default
title: "ارتباط با ما"
permalink: /contact/
---

# ارتباط با ما

اگر سوال، پیشنهاد یا فایل برای ما دارید، از فرم زیر استفاده کنید.

<div id="form-status" style="display:none;margin:16px 0;padding:14px 16px;border-radius:14px;background:#dff7ea;color:#14532d;font-weight:700;">
  پیام شما دریافت شد.
</div>

<form id="contact-form" action="https://formspree.io/f/mvzvkgjg" method="POST" style="display:grid;gap:16px;margin-top:24px;background:var(--surface);border:1px solid var(--border);border-radius:20px;padding:24px;">
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

  <button type="submit" id="submit-btn" style="border:none;border-radius:999px;padding:14px 18px;background:var(--primary);color:white;font:inherit;font-weight:800;cursor:pointer;">
    ارسال پیام
  </button>
</form>

<script>
  const form = document.getElementById('contact-form');
  const statusBox = document.getElementById('form-status');
  const submitBtn = document.getElementById('submit-btn');

  form.addEventListener('submit', async function (e) {
    e.preventDefault();

    submitBtn.disabled = true;
    submitBtn.textContent = 'در حال ارسال...';

    const data = new FormData(form);

    try {
      const response = await fetch(form.action, {
        method: 'POST',
        body: data,
        headers: {
          'Accept': 'application/json'
        }
      });

      if (response.ok) {
        form.reset();
        statusBox.style.display = 'block';
        statusBox.textContent = 'پیام شما دریافت شد.';
      } else {
        statusBox.style.display = 'block';
        statusBox.style.background = '#fee2e2';
        statusBox.style.color = '#991b1b';
        statusBox.textContent = 'ارسال پیام انجام نشد. دوباره تلاش کنید.';
      }
    } catch (err) {
      statusBox.style.display = 'block';
      statusBox.style.background = '#fee2e2';
      statusBox.style.color 
