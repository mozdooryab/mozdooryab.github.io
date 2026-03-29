---
layout: default
title: "ارتباط با ما"
permalink: /contact/
---

# ارتباط با ما

اگر سوال یا پیشنهادی دارید، از فرم زیر استفاده کنید.

<div id="form-status" style="display:none;margin:16px 0;padding:14px 16px;border-radius:14px;font-weight:700;"></div>

<form id="contact-form" style="display:grid;gap:16px;margin-top:24px;background:var(--surface);border:1px solid var(--border);border-radius:20px;padding:24px;">
  <input type="hidden" name="access_key" value="ee3cebe3-80ad-4b98-8a06-3f09e4b342a6">
  <input type="hidden" name="subject" value="پیام جدید از صفحه تماس">
  <input type="hidden" name="from_name" value="وب‌سایت من">
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
  const form = document.getElementById("contact-form");
  const statusBox = document.getElementById("form-status");
  const submitBtn = document.getElementById("submit-btn");

  form.addEventListener("submit", async function (e) {
    e.preventDefault();

    submitBtn.disabled = true;
    submitBtn.textContent = "در حال ارسال...";

    const formData = new FormData(form);
    const object = Object.fromEntries(formData);
    const json = JSON.stringify(object);

    try {
      const response = await fetch("https://api.web3forms.com/submit", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "Accept": "application/json"
        },
        body: json
      });

      const result = await response.json();

      if (result.success) {
        form.reset();
        statusBox.style.display = "block";
        statusBox.style.background = "#dff7ea";
        statusBox.style.color = "#14532d";
        statusBox.textContent = "پیام شما دریافت شد.";
      } else {
        statusBox.style.display = "block";
        statusBox.style.background = "#fee2e2";
        statusBox.style.color = "#991b1b";
        statusBox.textContent = result.message || "ارسال پیام انجام نشد.";
      }
    } catch (error) {
      statusBox.style.display = "block";
      statusBox.style.background = "#fee2e2";
      statusBox.style.color = "#991b1b";
      statusBox.textContent = "خطا در ارسال فرم.";
    }

    submitBtn.disabled = false;
    submitBtn.textContent = "ارسال پیام";
  });
</script>
