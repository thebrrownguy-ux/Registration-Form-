<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Quantum University Roorkee — Student Details Form</title>
  <style>
    :root {
      --bg: #ffffff;            /* white background */
      --panel: #f7f7f7;         /* light panel */
      --accent: #6a4cff;        /* bright violet accent */
      --accent-2: #4b2aff;      /* darker accent */
      --text: #000000;          /* primary text */
      --muted: #444444;         /* subtle text */
      --error: #ff5c7a;         /* error color */
      --ok: #2ad1a3;            /* success color */
      --border: #cccccc;        /* panel border */
      --focus-ring: 0 0 0 3px rgba(106, 76, 255, 0.35);
      --radius-xl: 16px;
      --radius-2xl: 20px;
    }

    * { box-sizing: border-box; }

    html, body {
      height: 100%;
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: var(--bg);
      color: var(--text);
    }

    .wrapper {
      min-height: 100%;
      display: grid;
      grid-template-rows: auto 1fr auto;
    }

    header {
      padding: 28px 20px;
      border-bottom: 1px solid var(--border);
      background: var(--panel);
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .brand {
      max-width: 1100px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .brand-mark {
      width: 40px; height: 40px;
      border-radius: 12px;
      background: conic-gradient(from 180deg at 50% 50%, #6a4cff, #a897ff, #6a4cff);
      box-shadow: 0 6px 20px rgba(106,76,255,0.25);
    }

    .brand h1 {
      font-size: 1.25rem;
      letter-spacing: 0.04em;
      margin: 0;
      font-weight: 700;
    }

    main {
      max-width: 1100px;
      margin: 32px auto;
      padding: 0 16px 40px;
      width: 100%;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--border);
      border-radius: var(--radius-2xl);
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      overflow: hidden;
    }

    .card-head {
      padding: 22px 22px 0;
    }

    .subtitle {
      margin: 0 0 8px 0;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .title {
      margin: 0 0 8px 0;
      font-size: 1.6rem;
      font-weight: 700;
    }

    .hint {
      margin: 0 0 20px 0;
      color: var(--muted);
      font-size: 0.92rem;
    }

    form {
      display: grid;
      gap: 18px;
      padding: 22px;
      grid-template-columns: repeat(12, 1fr);
    }

    .field {
      grid-column: span 12;
      display: grid;
      gap: 8px;
    }

    .field.half { grid-column: span 6; }
    .field.third { grid-column: span 4; }

    label {
      font-size: 0.95rem;
      color: var(--muted);
    }

    input[type="text"],
    input[type="number"],
    textarea,
    select {
      width: 100%;
      padding: 12px 14px;
      border-radius: 12px;
      border: 1px solid var(--border);
      background: #fff;
      color: var(--text);
      outline: none;
      transition: box-shadow 0.15s ease, border-color 0.15s ease, transform 0.04s ease;
    }

    textarea { resize: vertical; min-height: 96px; }

    input:focus, textarea:focus, select:focus {
      box-shadow: var(--focus-ring);
      border-color: var(--accent);
    }

    .radio-group {
      display: flex;
      flex-wrap: wrap;
      gap: 14px 24px;
      padding: 8px 2px 2px;
    }

    .radio {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .radio input { accent-color: var(--accent); }

    .controls {
      display: flex;
      gap: 12px;
      padding: 0 22px 22px;
      border-top: 1px solid var(--border);
      justify-content: flex-end;
    }

    button {
      appearance: none;
      border: none;
      border-radius: 12px;
      padding: 12px 18px;
      font-weight: 600;
      letter-spacing: 0.02em;
      cursor: pointer;
      transition: transform 0.06s ease, box-shadow 0.15s ease, opacity 0.15s ease;
    }

    .btn-primary {
      background: linear-gradient(180deg, #6a4cff, #5d3af7);
      color: #fff;
      box-shadow: 0 6px 18px rgba(106,76,255,0.3);
    }

    .btn-secondary {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
    }

    .note {
      font-size: 0.85rem;
      color: var(--muted);
    }

    .status {
      display: none;
      margin: 18px 22px 0;
      padding: 12px 14px;
      border-radius: 12px;
      border: 1px solid var(--border);
      background: #fff;
    }

    .status.ok { display: block; border-color: rgba(42,209,163,0.45); }
    .status.err { display: block; border-color: rgba(255,92,122,0.45); }

    .status strong.ok { color: var(--ok); }
    .status strong.err { color: var(--error); }

    footer {
      padding: 24px 20px 40px;
      color: var(--muted);
      text-align: center;
      font-size: 0.85rem;
    }

    @media (max-width: 850px) {
      .field.half, .field.third { grid-column: span 12; }
      .title { font-size: 1.35rem; }
    }
  </style>
</head>
<body>
  <div class="wrapper">
    <header aria-label="Institution Header">
      <div class="brand">
        <div class="brand-mark" aria-hidden="true"></div>
        <h1>Quantum University Roorkee</h1>
      </div>
    </header>

    <main>
      <section class="card" aria-labelledby="form-title">
        <div class="card-head">
          <p class="subtitle">Formal Submission</p>
          <h2 id="form-title" class="title">Student Details Form</h2>
          <p class="hint">Please fill in all required fields carefully. Ensure information is accurate before submitting.</p>
        </div>
        <form id="student-form" novalidate>
          <div class="field half">
            <label for="name">Full Name <span aria-hidden="true">*</span></label>
            <input id="name" name="name" type="text" placeholder="e.g., Ayaan Sharma" autocomplete="name" required />
          </div>

          <div class="field third">
            <label for="class">Class / Program <span aria-hidden="true">*</span></label>
            <select id="class" name="class" required>
              <option value="" selected disabled>Select</option>
              <option>UG — B.Tech</option>
              <option>UG — B.Sc</option>
              <option>UG — BBA</option>
              <option>PG — M.Tech</option>
              <option>PG — MBA</option>
              <option>PG — M.Sc</option>
              <option>PhD</option>
              <option>Other</option>
            </select>
          </div>

          <div class="field third">
            <label for="subject">Subject / Major <span aria-hidden="true">*</span></label>
            <input id="subject" name="subject" type="text" placeholder="e.g., Computer Science" required />
          </div>

          <div class="field third">
            <label for="roll">Roll Number <span aria-hidden="true">*</span></label>
            <input id="roll" name="roll" type="text" placeholder="e.g., QUR-23-0451" inputmode="numeric" required />
          </div>

          <div class="field">
            <label for="address">Address <span aria-hidden="true">*</span></label>
            <textarea id="address" name="address" placeholder="House No., Street, Area, City, State, PIN" required></textarea>
          </div>

          <div class="field half">
            <label>Gender <span aria-hidden="true">*</span></label>
            <div class="radio-group" role="radiogroup" aria-label="Gender">
              <label class="radio"><input type="radio" name="gender" value="Female" required /> Female</label>
              <label class="radio"><input type="radio" name="gender" value="Male" /> Male</label>
              <label class="radio"><input type="radio" name="gender" value="Non-binary" /> Non-binary</label>
              <label class="radio"><input type="radio" name="gender" value="Prefer not to say" /> Prefer not to say</label>
              <label class="radio"><input type="radio" name="gender" value="Self-describe" /> Self-describe</label>
            </div>
          </div>

          <div class="field half">
            <label for="other">Additional Information (optional)</label>
            <textarea id="other" name="other" placeholder="Any notes or relevant details you'd like to add"></textarea>
          </div>

          <div class="field half">
            <label for="funny">D* Size</label>
            <input id="funny" name="funny" type="number" step="0.1" min="0" placeholder="Enter a number" />
           
          </div>

          <div id="form-status" class="status" aria-live="polite"></div>

          <div class="controls">
            <button type="reset" class="btn-secondary" aria-label="Reset form">Reset</button>
            <button type="submit" class="btn-primary" aria-label="Submit form">Submit</button>
          </div>
        </form>
      </section>
    </main>

    <footer>
      © <span id="year"></span> Quantum University Roorkee · All rights reserved
    </footer>
  </div>

  <script>
    (function () {
      const byId = (id) => document.getElementById(id);
      const form = byId('student-form');
      const status = byId('form-status');
      byId('year').textContent = new Date().getFullYear();

      function showStatus(type, message) {
        status.className = 'status ' + (type === 'ok' ? 'ok' : 'err');
        status.innerHTML = `<strong class="${type}">${type === 'ok' ? 'Success:' : 'Please check:'}</strong> ${message}`;
      }

      function validate() {
        const requiredFields = ['name', 'class', 'subject', 'roll', 'address'];
        for (const id of requiredFields) {
          const el = byId(id);
          if (!el) continue;
          const val = (el.value || '').trim();
          if (!val) {
            el.focus();
            showStatus('err', `“${el.previousElementSibling?.textContent.replace('*','').trim()}” is required.`);
            return false;
          }
        }
        const genderChecked = !!document.querySelector('input[name="gender"]:checked');
        if (!genderChecked) {
          showStatus('err', 'Please select your gender.');
          return false;
        }
        return true;
      }

      form.addEventListener('submit', function (e) {
        e.preventDefault();
        if (!validate()) return;

        const formData = new FormData(form);
        const payload = Object.fromEntries(formData.entries());
        console.log('Submitting form payload:', payload);
        showStatus('ok', 'Your details have been recorded. You may close this window.');
        form.reset();
      });

      form.addEventListener('reset', function () {
        status.className = 'status';
        status.textContent = '';
      });
    })();
  </script>
</body>
</html>
