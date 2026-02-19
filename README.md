<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>JVN AI – Rwanda CBC Teacher Assistant</title>
<link rel="canonical" href="https://javanhury-dotcom.github.io/jvn-ai/">
<meta property="og:title" content="JVN AI – Rwanda CBC Teacher Assistant">
<meta property="og:description" content="AI-powered Rwanda CBC curriculum assistant for lesson plans, schemes of work, quizzes, unit plans, class notes and more.">
<meta property="og:url" content="https://javanhury-dotcom.github.io/jvn-ai/">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="JVN AI – Rwanda CBC Teacher Assistant">
<meta name="twitter:description" content="AI-powered Rwanda CBC curriculum assistant for all grade levels.">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #0a7c4f;
    --green-light: #12a869;
    --green-pale: #e8f5ee;
    --gold: #d4a017;
    --gold-light: #f0c040;
    --blue: #1b4f8a;
    --cream: #faf8f3;
    --dark: #1a1a1a;
    --mid: #4a4a4a;
    --border: #e0ddd6;
    --white: #ffffff;
    --sidebar-width: 280px;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Plus Jakarta Sans', sans-serif;
    background: var(--cream);
    color: var(--dark);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  /* ── HEADER ── */
  header {
    background: var(--green);
    color: white;
    padding: 0 2rem;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 12px rgba(0,0,0,0.18);
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .logo-icon {
    width: 38px;
    height: 38px;
    background: var(--gold);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }

  .logo-text {
    font-family: 'DM Serif Display', serif;
    font-size: 1.5rem;
    letter-spacing: -0.5px;
  }

  .logo-text span {
    color: var(--gold-light);
  }

  .header-sub {
    font-size: 0.7rem;
    opacity: 0.75;
    font-weight: 300;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-top: 2px;
  }

  .header-right {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .grade-badge {
    background: rgba(255,255,255,0.15);
    border: 1px solid rgba(255,255,255,0.25);
    border-radius: 20px;
    padding: 4px 14px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  .user-avatar {
    width: 36px;
    height: 36px;
    background: var(--gold);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 0.9rem;
    color: var(--dark);
    cursor: pointer;
  }

  /* ── MAIN LAYOUT ── */
  .app-body {
    display: flex;
    flex: 1;
    min-height: calc(100vh - 64px);
  }

  /* ── SIDEBAR ── */
  .sidebar {
    width: var(--sidebar-width);
    background: white;
    border-right: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    padding: 1.5rem 0;
    overflow-y: auto;
    flex-shrink: 0;
  }

  .sidebar-section-label {
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #999;
    padding: 0 1.25rem;
    margin-bottom: 0.5rem;
    margin-top: 1.25rem;
  }

  .sidebar-section-label:first-child { margin-top: 0; }

  .nav-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 0.6rem 1.25rem;
    cursor: pointer;
    border-radius: 0;
    transition: all 0.18s;
    font-size: 0.88rem;
    font-weight: 500;
    color: var(--mid);
    border-left: 3px solid transparent;
    position: relative;
  }

  .nav-item:hover {
    background: var(--green-pale);
    color: var(--green);
  }

  .nav-item.active {
    background: var(--green-pale);
    color: var(--green);
    border-left: 3px solid var(--green);
    font-weight: 600;
  }

  .nav-icon { font-size: 1.1rem; width: 22px; text-align: center; }

  .nav-badge {
    margin-left: auto;
    background: var(--green);
    color: white;
    border-radius: 10px;
    padding: 1px 8px;
    font-size: 0.65rem;
    font-weight: 700;
  }

  .sidebar-grade-selector {
    padding: 0 1.25rem;
    margin-bottom: 0.25rem;
  }

  .sidebar-grade-selector select {
    width: 100%;
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 7px 10px;
    font-size: 0.82rem;
    font-family: 'Plus Jakarta Sans', sans-serif;
    color: var(--dark);
    background: var(--cream);
    cursor: pointer;
    outline: none;
  }

  .sidebar-grade-selector select:focus {
    border-color: var(--green);
  }

  /* ── MAIN CONTENT ── */
  .main-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  /* ── TOOL PANEL ── */
  .tool-panel {
    display: none;
    flex-direction: column;
    flex: 1;
    overflow: hidden;
  }

  .tool-panel.active { display: flex; }

  .tool-header {
    padding: 1.5rem 2rem 1rem;
    border-bottom: 1px solid var(--border);
    background: white;
  }

  .tool-header h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.6rem;
    color: var(--dark);
    margin-bottom: 4px;
  }

  .tool-header p {
    font-size: 0.85rem;
    color: #888;
  }

  /* ── CHAT AREA ── */
  .chat-area {
    flex: 1;
    overflow-y: auto;
    padding: 1.5rem 2rem;
    display: flex;
    flex-direction: column;
    gap: 1.25rem;
  }

  .msg {
    display: flex;
    gap: 12px;
    animation: msgIn 0.3s ease;
    max-width: 820px;
  }

  @keyframes msgIn {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .msg.user { flex-direction: row-reverse; align-self: flex-end; }

  .msg-avatar {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .msg.ai .msg-avatar { background: var(--green); }
  .msg.user .msg-avatar { background: var(--gold); color: var(--dark); font-weight: 700; font-size: 0.85rem; font-family: 'Plus Jakarta Sans', sans-serif; }

  .msg-bubble {
    background: white;
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1rem 1.2rem;
    font-size: 0.88rem;
    line-height: 1.65;
    color: var(--dark);
    max-width: 680px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.05);
  }

  .msg.user .msg-bubble {
    background: var(--green);
    color: white;
    border-color: var(--green);
  }

  .msg-bubble h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.05rem;
    margin-bottom: 8px;
    color: var(--green);
  }

  .msg.user .msg-bubble h3 { color: var(--gold-light); }

  .msg-bubble .doc-block {
    background: var(--green-pale);
    border: 1px solid #b8ddc8;
    border-radius: 10px;
    padding: 1rem;
    margin-top: 10px;
    font-size: 0.84rem;
  }

  .msg-bubble .doc-block h4 {
    font-weight: 700;
    color: var(--green);
    margin-bottom: 6px;
    font-size: 0.88rem;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .msg-bubble table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 8px;
    font-size: 0.82rem;
  }

  .msg-bubble table th {
    background: var(--green);
    color: white;
    padding: 6px 10px;
    text-align: left;
    font-weight: 600;
  }

  .msg-bubble table td {
    padding: 6px 10px;
    border-bottom: 1px solid #e5e5e5;
    vertical-align: top;
  }

  .msg-bubble table tr:nth-child(even) td { background: #f5faf7; }

  .msg-bubble ul, .msg-bubble ol {
    padding-left: 1.2rem;
    margin: 6px 0;
  }

  .msg-bubble li { margin-bottom: 4px; }

  .copy-btn {
    margin-top: 10px;
    background: none;
    border: 1px solid #ccc;
    border-radius: 6px;
    padding: 4px 12px;
    font-size: 0.75rem;
    cursor: pointer;
    color: #666;
    font-family: 'Plus Jakarta Sans', sans-serif;
    transition: all 0.2s;
  }

  .copy-btn:hover { border-color: var(--green); color: var(--green); }

  /* ── INPUT BAR ── */
  .input-bar {
    padding: 1rem 2rem 1.25rem;
    background: white;
    border-top: 1px solid var(--border);
  }

  .quick-prompts {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 10px;
  }

  .qp-btn {
    background: var(--green-pale);
    border: 1px solid #b8ddc8;
    border-radius: 20px;
    padding: 5px 14px;
    font-size: 0.77rem;
    cursor: pointer;
    color: var(--green);
    font-weight: 600;
    font-family: 'Plus Jakarta Sans', sans-serif;
    transition: all 0.18s;
    white-space: nowrap;
  }

  .qp-btn:hover {
    background: var(--green);
    color: white;
    border-color: var(--green);
  }

  .input-row {
    display: flex;
    gap: 10px;
    align-items: flex-end;
  }

  .input-controls {
    display: flex;
    gap: 8px;
    align-items: center;
    margin-bottom: 4px;
  }

  .ctrl-select {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 5px 10px;
    font-size: 0.78rem;
    font-family: 'Plus Jakarta Sans', sans-serif;
    color: var(--dark);
    background: var(--cream);
    cursor: pointer;
    outline: none;
  }

  .ctrl-select:focus { border-color: var(--green); }

  .input-wrap {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  textarea#chatInput {
    width: 100%;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    padding: 0.75rem 1rem;
    font-size: 0.88rem;
    font-family: 'Plus Jakarta Sans', sans-serif;
    resize: none;
    min-height: 52px;
    max-height: 150px;
    outline: none;
    background: var(--cream);
    color: var(--dark);
    transition: border-color 0.2s;
  }

  textarea#chatInput:focus { border-color: var(--green); background: white; }

  .send-btn {
    background: var(--green);
    color: white;
    border: none;
    border-radius: 12px;
    width: 48px;
    height: 48px;
    cursor: pointer;
    font-size: 1.2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: background 0.2s;
    align-self: flex-end;
  }

  .send-btn:hover { background: var(--green-light); }
  .send-btn:disabled { background: #ccc; cursor: not-allowed; }

  /* ── TYPING INDICATOR ── */
  .typing-indicator {
    display: flex;
    gap: 12px;
    max-width: 820px;
  }

  .typing-dots {
    background: white;
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 0.85rem 1.1rem;
    display: flex;
    gap: 5px;
    align-items: center;
  }

  .dot {
    width: 7px; height: 7px;
    background: var(--green);
    border-radius: 50%;
    animation: bounce 1.2s infinite;
  }

  .dot:nth-child(2) { animation-delay: 0.2s; }
  .dot:nth-child(3) { animation-delay: 0.4s; }

  @keyframes bounce {
    0%, 60%, 100% { transform: translateY(0); }
    30% { transform: translateY(-7px); }
  }

  /* ── RESOURCE LIBRARY PANEL ── */
  .resource-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 1rem;
    padding: 1.5rem 2rem;
    overflow-y: auto;
    flex: 1;
  }

  .resource-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.25rem;
    cursor: pointer;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }

  .resource-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 4px;
    background: var(--green);
  }

  .resource-card:hover {
    border-color: var(--green);
    box-shadow: 0 4px 20px rgba(10,124,79,0.12);
    transform: translateY(-2px);
  }

  .resource-card .rc-icon { font-size: 2rem; margin-bottom: 10px; }

  .resource-card h3 {
    font-size: 0.92rem;
    font-weight: 700;
    margin-bottom: 4px;
    color: var(--dark);
  }

  .resource-card p {
    font-size: 0.78rem;
    color: #888;
    line-height: 1.4;
  }

  .resource-card .rc-meta {
    margin-top: 12px;
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
  }

  .tag {
    background: var(--green-pale);
    color: var(--green);
    border-radius: 6px;
    padding: 2px 8px;
    font-size: 0.7rem;
    font-weight: 600;
  }

  /* ── QUIZ BUILDER ── */
  .quiz-builder {
    padding: 1.5rem 2rem;
    overflow-y: auto;
    flex: 1;
  }

  .form-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    max-width: 700px;
  }

  .form-card h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.3rem;
    margin-bottom: 1.25rem;
    color: var(--dark);
    padding-bottom: 0.75rem;
    border-bottom: 1px solid var(--border);
  }

  .form-group {
    margin-bottom: 1rem;
  }

  .form-group label {
    display: block;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--mid);
    margin-bottom: 5px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .form-group input,
  .form-group select,
  .form-group textarea {
    width: 100%;
    border: 1.5px solid var(--border);
    border-radius: 10px;
    padding: 9px 12px;
    font-size: 0.85rem;
    font-family: 'Plus Jakarta Sans', sans-serif;
    color: var(--dark);
    background: var(--cream);
    outline: none;
    transition: border-color 0.2s;
  }

  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus { border-color: var(--green); background: white; }

  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .generate-btn {
    background: var(--green);
    color: white;
    border: none;
    border-radius: 10px;
    padding: 11px 28px;
    font-size: 0.9rem;
    font-weight: 700;
    font-family: 'Plus Jakarta Sans', sans-serif;
    cursor: pointer;
    transition: background 0.2s;
    margin-top: 6px;
  }

  .generate-btn:hover { background: var(--green-light); }

  /* ── CBC SUBJECTS REFERENCE ── */
  .subjects-panel {
    padding: 1.5rem 2rem;
    overflow-y: auto;
    flex: 1;
  }

  .subject-group {
    margin-bottom: 2rem;
  }

  .subject-group h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.15rem;
    color: var(--green);
    margin-bottom: 0.75rem;
    padding-bottom: 4px;
    border-bottom: 2px solid var(--green-pale);
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .subject-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .subject-tag {
    background: white;
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 6px 14px;
    font-size: 0.82rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.18s;
    color: var(--dark);
  }

  .subject-tag:hover {
    background: var(--green);
    color: white;
    border-color: var(--green);
  }

  /* ── WELCOME SCREEN ── */
  .welcome-screen {
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
  }

  .welcome-card {
    max-width: 640px;
    text-align: center;
  }

  .welcome-card .wc-flag { font-size: 3.5rem; margin-bottom: 1rem; }

  .welcome-card h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 2.2rem;
    color: var(--dark);
    margin-bottom: 0.5rem;
    line-height: 1.2;
  }

  .welcome-card h1 span { color: var(--green); }

  .welcome-card p {
    font-size: 0.95rem;
    color: #666;
    line-height: 1.65;
    margin-bottom: 2rem;
  }

  .welcome-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    text-align: left;
    margin-bottom: 2rem;
  }

  .wg-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.1rem;
    cursor: pointer;
    transition: all 0.2s;
  }

  .wg-card:hover {
    border-color: var(--green);
    box-shadow: 0 4px 16px rgba(10,124,79,0.1);
    transform: translateY(-2px);
  }

  .wg-card .wc-icon { font-size: 1.6rem; margin-bottom: 6px; }
  .wg-card h3 { font-size: 0.88rem; font-weight: 700; margin-bottom: 3px; }
  .wg-card p { font-size: 0.77rem; color: #888; }

  .start-btn {
    background: var(--green);
    color: white;
    border: none;
    border-radius: 12px;
    padding: 13px 36px;
    font-size: 0.95rem;
    font-weight: 700;
    font-family: 'Plus Jakarta Sans', sans-serif;
    cursor: pointer;
    transition: background 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .start-btn:hover { background: var(--green-light); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: #ccc; border-radius: 10px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--green); }

  /* ── TOAST ── */
  .toast {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: var(--dark);
    color: white;
    padding: 10px 20px;
    border-radius: 10px;
    font-size: 0.82rem;
    z-index: 999;
    opacity: 0;
    transform: translateY(10px);
    transition: all 0.25s;
    pointer-events: none;
  }

  .toast.show { opacity: 1; transform: translateY(0); }

  /* ── MODAL OVERLAY ── */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(10,30,20,0.55);
    backdrop-filter: blur(4px);
    z-index: 500;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }
  .modal-overlay.open { display: flex; }

  .modal {
    background: white;
    border-radius: 20px;
    width: 100%;
    max-width: 480px;
    max-height: 92vh;
    overflow-y: auto;
    box-shadow: 0 24px 80px rgba(0,0,0,0.25);
    animation: modalIn 0.3s cubic-bezier(.34,1.56,.64,1);
  }

  @keyframes modalIn {
    from { opacity:0; transform: scale(0.92) translateY(20px); }
    to   { opacity:1; transform: scale(1) translateY(0); }
  }

  .modal-header {
    padding: 1.5rem 1.5rem 1rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
  }

  .modal-header h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.4rem;
    color: var(--dark);
  }

  .modal-header p { font-size: 0.8rem; color: #888; margin-top: 3px; }

  .modal-close {
    background: none;
    border: none;
    font-size: 1.3rem;
    cursor: pointer;
    color: #aaa;
    padding: 2px 6px;
    border-radius: 6px;
    transition: all 0.2s;
    line-height: 1;
  }
  .modal-close:hover { background: #f0f0f0; color: var(--dark); }

  .modal-body { padding: 1.25rem 1.5rem; }

  .modal-footer {
    padding: 1rem 1.5rem 1.5rem;
    border-top: 1px solid var(--border);
    display: flex;
    gap: 10px;
    justify-content: flex-end;
  }

  /* ── AUTH TABS ── */
  .auth-tabs {
    display: flex;
    border-bottom: 2px solid var(--border);
    margin-bottom: 1.25rem;
  }

  .auth-tab {
    flex: 1;
    padding: 10px;
    text-align: center;
    cursor: pointer;
    font-size: 0.85rem;
    font-weight: 600;
    color: #999;
    border-bottom: 2px solid transparent;
    margin-bottom: -2px;
    transition: all 0.2s;
  }

  .auth-tab.active {
    color: var(--green);
    border-bottom-color: var(--green);
  }

  .auth-form { display: none; }
  .auth-form.active { display: block; }

  /* ── STEPS ── */
  .steps-bar {
    display: flex;
    align-items: center;
    gap: 6px;
    margin-bottom: 1.5rem;
  }

  .step-dot {
    width: 28px; height: 28px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.72rem; font-weight: 700;
    background: #eee; color: #999;
    transition: all 0.3s;
    flex-shrink: 0;
  }

  .step-dot.active { background: var(--green); color: white; }
  .step-dot.done { background: var(--green-pale); color: var(--green); }

  .step-line {
    flex: 1; height: 2px;
    background: #eee; border-radius: 2px;
    transition: background 0.3s;
  }

  .step-line.done { background: var(--green); }

  .step-label {
    font-size: 0.7rem; color: #aaa; text-align: center;
    margin-top: 3px;
  }

  .step-page { display: none; }
  .step-page.active { display: block; }

  /* ── PLAN CARDS ── */
  .plans-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 10px;
    margin-bottom: 1rem;
  }

  .plan-card {
    border: 2px solid var(--border);
    border-radius: 14px;
    padding: 1rem 0.75rem;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
    position: relative;
  }

  .plan-card:hover { border-color: var(--green); }

  .plan-card.selected {
    border-color: var(--green);
    background: var(--green-pale);
  }

  .plan-card .plan-badge {
    position: absolute;
    top: -10px; left: 50%; transform: translateX(-50%);
    background: var(--gold);
    color: var(--dark);
    font-size: 0.62rem;
    font-weight: 800;
    padding: 2px 10px;
    border-radius: 10px;
    white-space: nowrap;
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }

  .plan-card .plan-icon { font-size: 1.5rem; margin-bottom: 6px; }

  .plan-card .plan-name {
    font-weight: 700; font-size: 0.82rem;
    color: var(--dark); margin-bottom: 4px;
  }

  .plan-card .plan-price {
    font-family: 'DM Serif Display', serif;
    font-size: 1.25rem;
    color: var(--green);
    line-height: 1;
  }

  .plan-card .plan-period {
    font-size: 0.68rem; color: #999; margin-top: 2px;
  }

  .plan-card .plan-features {
    margin-top: 8px;
    font-size: 0.7rem;
    color: #666;
    line-height: 1.6;
    text-align: left;
  }

  /* ── MOMO PAYMENT ── */
  .momo-box {
    background: linear-gradient(135deg, #ffcc00 0%, #ffa500 100%);
    border-radius: 16px;
    padding: 1.25rem;
    margin-bottom: 1rem;
    position: relative;
    overflow: hidden;
  }

  .momo-box::before {
    content: '';
    position: absolute;
    top: -20px; right: -20px;
    width: 80px; height: 80px;
    background: rgba(255,255,255,0.15);
    border-radius: 50%;
  }

  .momo-box::after {
    content: '';
    position: absolute;
    bottom: -30px; right: 20px;
    width: 100px; height: 100px;
    background: rgba(255,255,255,0.1);
    border-radius: 50%;
  }

  .momo-logo {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 12px;
  }

  .momo-logo-icon {
    width: 42px; height: 42px;
    background: white;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.4rem;
    box-shadow: 0 2px 8px rgba(0,0,0,0.15);
    flex-shrink: 0;
  }

  .momo-logo-text { font-weight: 800; font-size: 1rem; color: #1a1a1a; line-height: 1.2; }
  .momo-logo-sub { font-size: 0.7rem; color: rgba(0,0,0,0.6); }

  .momo-amount {
    font-family: 'DM Serif Display', serif;
    font-size: 2rem;
    color: #1a1a1a;
    line-height: 1;
    margin-bottom: 4px;
  }

  .momo-amount-label {
    font-size: 0.75rem; color: rgba(0,0,0,0.6);
  }

  .momo-steps {
    margin-top: 1rem;
    background: rgba(255,255,255,0.3);
    border-radius: 10px;
    padding: 0.75rem;
  }

  .momo-step {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    margin-bottom: 8px;
    font-size: 0.78rem;
    color: #1a1a1a;
  }

  .momo-step:last-child { margin-bottom: 0; }

  .momo-step-num {
    width: 20px; height: 20px;
    background: rgba(0,0,0,0.15);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.65rem; font-weight: 800;
    flex-shrink: 0;
  }

  .momo-input-group {
    margin-bottom: 1rem;
  }

  .momo-input-group label {
    display: block;
    font-size: 0.78rem; font-weight: 700;
    color: var(--mid);
    margin-bottom: 5px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .momo-input-group input {
    width: 100%;
    border: 1.5px solid var(--border);
    border-radius: 10px;
    padding: 10px 14px;
    font-size: 0.88rem;
    font-family: 'Plus Jakarta Sans', sans-serif;
    outline: none;
    background: var(--cream);
    transition: border-color 0.2s;
  }

  .momo-input-group input:focus { border-color: #ffa500; background: white; }

  .phone-prefix {
    display: flex;
    gap: 8px;
    align-items: center;
  }

  .prefix-badge {
    background: #ffa500;
    color: white;
    border-radius: 8px;
    padding: 10px 12px;
    font-weight: 700;
    font-size: 0.85rem;
    white-space: nowrap;
    flex-shrink: 0;
  }

  /* ── SUCCESS SCREEN ── */
  .success-screen {
    text-align: center;
    padding: 1.5rem 0;
  }

  .success-icon {
    width: 72px; height: 72px;
    background: var(--green-pale);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem;
    margin: 0 auto 1rem;
    animation: popIn 0.4s cubic-bezier(.34,1.56,.64,1);
  }

  @keyframes popIn {
    from { transform: scale(0); opacity: 0; }
    to   { transform: scale(1); opacity: 1; }
  }

  .success-screen h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 1.4rem;
    margin-bottom: 6px;
    color: var(--green);
  }

  .success-screen p { font-size: 0.85rem; color: #666; line-height: 1.6; }

  .teacher-card {
    background: var(--green);
    color: white;
    border-radius: 14px;
    padding: 1rem 1.25rem;
    margin: 1rem 0;
    text-align: left;
  }

  .teacher-card .tc-label { font-size: 0.65rem; opacity: 0.7; text-transform: uppercase; letter-spacing: 1px; }
  .teacher-card .tc-value { font-size: 0.92rem; font-weight: 600; margin-bottom: 8px; }
  .teacher-card .tc-id { font-family: 'DM Serif Display', serif; font-size: 1.2rem; color: var(--gold-light); }

  /* ── HEADER BTNS ── */
  .header-btn {
    background: rgba(255,255,255,0.15);
    border: 1px solid rgba(255,255,255,0.3);
    color: white;
    border-radius: 8px;
    padding: 6px 14px;
    font-size: 0.78rem;
    font-weight: 600;
    font-family: 'Plus Jakarta Sans', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
  }

  .header-btn:hover { background: rgba(255,255,255,0.25); }
  .header-btn.gold { background: var(--gold); border-color: var(--gold); color: var(--dark); }
  .header-btn.gold:hover { background: var(--gold-light); }

  /* ── TEACHER PROFILE BAR ── */
  .teacher-bar {
    display: none;
    background: var(--green-pale);
    border-bottom: 1px solid #b8ddc8;
    padding: 6px 2rem;
    font-size: 0.78rem;
    color: var(--green);
    font-weight: 600;
    align-items: center;
    gap: 12px;
  }

  .teacher-bar.visible { display: flex; }
  .teacher-bar span { color: #666; font-weight: 400; }

  .plan-pill {
    background: var(--gold);
    color: var(--dark);
    border-radius: 10px;
    padding: 2px 10px;
    font-size: 0.68rem;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  /* ── LOADING ── */
  .loading-bar {
    height: 3px;
    background: linear-gradient(90deg, var(--green), var(--gold), var(--green));
    background-size: 200% 100%;
    animation: shimmer 1.5s infinite;
    border-radius: 2px;
    margin-bottom: 0;
    display: none;
  }

  .loading-bar.active { display: block; }

  @keyframes shimmer {
    0% { background-position: 200% 0; }
    100% { background-position: -200% 0; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">
    <div class="logo-icon">🎓</div>
    <div>
      <div class="logo-text">JVN<span> AI</span></div>
      <div class="header-sub">Rwanda CBC Curriculum Assistant &nbsp;|&nbsp; javanhury-dotcom.github.io/jvn-ai</div>
    </div>
  </div>
  <div class="header-right">
    <div class="grade-badge" id="headerGrade">All Levels</div>
    <button class="header-btn" onclick="openModal('login')">🔑 Login</button>
    <button class="header-btn gold" onclick="openModal('subscribe')">⭐ Subscribe</button>
    <div class="user-avatar" id="userAvatar">T</div>
  </div>
</header>

<div class="loading-bar" id="loadingBar"></div>

<!-- TEACHER SESSION BAR -->
<div class="teacher-bar" id="teacherBar">
  👤 <strong id="tbName">Teacher</strong>
  <span>|</span> <span id="tbSchool">School</span>
  <span>|</span> <span id="tbGrade">Grade</span>
  <span style="margin-left:auto"></span>
  <span class="plan-pill" id="tbPlan">Free</span>
  <button class="header-btn" style="font-size:0.72rem;padding:4px 10px" onclick="openModal('subscribe')">Upgrade</button>
  <button class="header-btn" style="font-size:0.72rem;padding:4px 10px;background:rgba(220,50,50,0.1);border-color:#f88;color:#c00" onclick="logoutTeacher()">Logout</button>
</div>

<!-- ══════════════════════════════════════════
     MODAL: REGISTER / LOGIN
══════════════════════════════════════════ -->
<div class="modal-overlay" id="modal-login">
  <div class="modal">
    <div class="modal-header">
      <div>
        <h2>🎓 Welcome to JVN AI</h2>
        <p>Rwanda CBC Teacher Assistant</p>
      </div>
      <button class="modal-close" onclick="closeModal('login')">✕</button>
    </div>
    <div class="modal-body">
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchAuthTab('login-form')">🔑 Login</div>
        <div class="auth-tab" onclick="switchAuthTab('register-form')">📝 Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div class="auth-form active" id="login-form">
        <div class="form-group">
          <label>Email Address</label>
          <input type="email" id="login-email" placeholder="yourname@example.com">
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" id="login-password" placeholder="Enter your password">
        </div>
        <div style="text-align:right;margin-bottom:1rem">
          <a href="#" style="font-size:0.78rem;color:var(--green);text-decoration:none">Forgot password?</a>
        </div>
        <button class="generate-btn" style="width:100%;justify-content:center" onclick="loginTeacher()">🔑 Login to JVN AI</button>
        <p style="text-align:center;margin-top:1rem;font-size:0.78rem;color:#888">
          Don't have an account? <a href="#" style="color:var(--green);font-weight:600" onclick="switchAuthTab('register-form')">Register free</a>
        </p>
      </div>

      <!-- REGISTER FORM -->
      <div class="auth-form" id="register-form">
        <div class="form-row">
          <div class="form-group">
            <label>First Name</label>
            <input type="text" id="reg-firstname" placeholder="e.g. Javan">
          </div>
          <div class="form-group">
            <label>Last Name</label>
            <input type="text" id="reg-lastname" placeholder="e.g. Nduwamungu">
          </div>
        </div>
        <div class="form-group">
          <label>Email Address</label>
          <input type="email" id="reg-email" placeholder="yourname@example.com">
        </div>
        <div class="form-group">
          <label>Phone Number (MTN MoMo)</label>
          <div class="phone-prefix">
            <div class="prefix-badge" style="background:var(--green)">🇷🇼 +250</div>
            <input type="tel" id="reg-phone" placeholder="078 XXX XXXX" style="flex:1">
          </div>
        </div>
        <div class="form-group">
          <label>School Name</label>
          <input type="text" id="reg-school" placeholder="e.g. GS Gatebe, GS Nyenyeri…">
        </div>
        <div class="form-row">
          <div class="form-group">
            <label>District</label>
            <select id="reg-district">
              <option value="">Select district</option>
              <optgroup label="Kigali City">
                <option>Gasabo</option><option>Kicukiro</option><option>Nyarugenge</option>
              </optgroup>
              <optgroup label="Northern Province">
                <option>Burera</option><option>Gakenke</option><option>Gicumbi</option><option>Musanze</option><option>Rulindo</option>
              </optgroup>
              <optgroup label="Southern Province">
                <option>Gisagara</option><option>Huye</option><option>Kamonyi</option><option>Muhanga</option><option>Nyamagabe</option><option>Nyanza</option><option>Nyaruguru</option><option>Ruhango</option>
              </optgroup>
              <optgroup label="Eastern Province">
                <option>Bugesera</option><option>Gatsibo</option><option>Kayonza</option><option>Kirehe</option><option>Ngoma</option><option>Nyagatare</option><option>Rwamagana</option>
              </optgroup>
              <optgroup label="Western Province">
                <option>Karongi</option><option>Ngororero</option><option>Nyabihu</option><option>Nyamasheke</option><option>Rubavu</option><option>Rutsiro</option><option>Rusizi</option>
              </optgroup>
            </select>
          </div>
          <div class="form-group">
            <label>Subjects You Teach</label>
            <select id="reg-subject">
              <option>Mathematics</option><option>English</option>
              <option>Kinyarwanda</option><option>Science</option>
              <option>Social Studies</option><option>ICT</option>
              <option>Biology</option><option>Chemistry</option>
              <option>Physics</option><option>History</option>
              <option>Geography</option><option>Multiple subjects</option>
            </select>
          </div>
        </div>
        <div class="form-group">
          <label>Grade Levels You Teach</label>
          <select id="reg-gradelevel">
            <option>Lower Primary (P1–P3)</option>
            <option>Upper Primary (P4–P6)</option>
            <option>O-Level (S1–S3)</option>
            <option>A-Level (S4–S6)</option>
            <option>TVET</option>
            <option>Multiple levels</option>
          </select>
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" id="reg-password" placeholder="Create a strong password">
        </div>
        <button class="generate-btn" style="width:100%" onclick="registerTeacher()">📝 Create My Account</button>
        <p style="text-align:center;margin-top:0.75rem;font-size:0.72rem;color:#aaa">
          By registering you agree to JVN AI's terms of service.<br>Your data is stored securely.
        </p>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════
     MODAL: SUBSCRIPTION & MTN MOMO PAYMENT
══════════════════════════════════════════ -->
<div class="modal-overlay" id="modal-subscribe">
  <div class="modal" style="max-width:520px">
    <div class="modal-header">
      <div>
        <h2>⭐ Subscribe to JVN AI</h2>
        <p>Unlock full CBC curriculum tools</p>
      </div>
      <button class="modal-close" onclick="closeModal('subscribe')">✕</button>
    </div>
    <div class="modal-body">

      <!-- STEPS BAR -->
      <div>
        <div class="steps-bar">
          <div class="step-dot active" id="sdot-1">1</div>
          <div class="step-line" id="sline-1"></div>
          <div class="step-dot" id="sdot-2">2</div>
          <div class="step-line" id="sline-2"></div>
          <div class="step-dot" id="sdot-3">3</div>
        </div>
        <div style="display:flex;justify-content:space-between;margin-bottom:1.25rem;margin-top:-6px">
          <div class="step-label">Choose Plan</div>
          <div class="step-label">Pay via MoMo</div>
          <div class="step-label">Confirmed!</div>
        </div>
      </div>

      <!-- STEP 1: CHOOSE PLAN -->
      <div class="step-page active" id="sub-step-1">
        <div class="plans-grid">
          <div class="plan-card" onclick="selectPlan('Basic', 2000)" id="plan-Basic">
            <div class="plan-icon">🌱</div>
            <div class="plan-name">Basic</div>
            <div class="plan-price">2,000</div>
            <div class="plan-period">RWF / month</div>
            <div class="plan-features">
              ✅ Lesson Plans<br>
              ✅ Quizzes<br>
              ✅ Class Notes<br>
              ❌ Schemes of Work<br>
             
            </div>
          </div>
          <div class="plan-card selected" onclick="selectPlan('Pro', 5000)" id="plan-Pro">
            <div class="plan-badge">⭐ Popular</div>
            <div class="plan-icon">🚀</div>
            <div class="plan-name">Pro</div>
            <div class="plan-price">5,000</div>
            <div class="plan-period">RWF / month</div>
            <div class="plan-features">
              ✅ All Basic features<br>
              ✅ Schemes of Work<br>
             
              ✅ Slide Outlines<br>
              ✅ Priority AI
            </div>
          </div>
          <div class="plan-card" onclick="selectPlan('School', 15000)" id="plan-School">
            <div class="plan-icon">🏫</div>
            <div class="plan-name">School</div>
            <div class="plan-price">15,000</div>
            <div class="plan-period">RWF / month</div>
            <div class="plan-features">
              ✅ All Pro features<br>
              ✅ Up to 10 teachers<br>
              ✅ Admin dashboard<br>
              ✅ Custom branding<br>
              ✅ WhatsApp support
            </div>
          </div>
        </div>
        <div style="background:var(--green-pale);border-radius:10px;padding:10px 14px;font-size:0.78rem;color:var(--green);display:flex;align-items:center;gap:8px;margin-bottom:1rem">
          🔒 <strong>7-day free trial</strong> on all plans — cancel anytime
        </div>
        <button class="generate-btn" style="width:100%" onclick="goSubStep(2)">Continue to Payment →</button>
      </div>

      <!-- STEP 2: MTN MOMO PAYMENT -->
      <div class="step-page" id="sub-step-2">
        <div class="momo-box">
          <div class="momo-logo">
            <div class="momo-logo-icon">📱</div>
            <div>
              <div class="momo-logo-text">MTN Mobile Money</div>
              <div class="momo-logo-sub">Rwanda — Secure Payment</div>
            </div>
          </div>
          <div class="momo-amount" id="momoAmount">5,000 RWF</div>
          <div class="momo-amount-label">Total due today — <span id="momoplan">Pro Plan</span></div>
          <div class="momo-steps">
            <div class="momo-step">
              <div class="momo-step-num">1</div>
              <div>Enter your MTN MoMo number below and click <strong>"Send Payment Request"</strong></div>
            </div>
            <div class="momo-step">
              <div class="momo-step-num">2</div>
              <div>You'll receive a <strong>prompt on your phone</strong> — enter your MoMo PIN to confirm</div>
            </div>
            <div class="momo-step">
              <div class="momo-step-num">3</div>
              <div>Payment goes directly to <strong>JVN AI account</strong> — your subscription activates instantly</div>
            </div>
          </div>
        </div>

        <div class="momo-input-group">
          <label>Your MTN MoMo Phone Number</label>
          <div class="phone-prefix">
            <div class="prefix-badge">🇷🇼 +250</div>
            <input type="tel" id="momo-phone" placeholder="078 XXX XXXX" style="flex:1">
          </div>
        </div>

        <div class="momo-input-group">
          <label>Full Name (as registered on MoMo)</label>
          <input type="text" id="momo-name" placeholder="e.g. Javan Nduwamungu">
        </div>

        <div style="background:#fff8e6;border:1px solid #ffd970;border-radius:10px;padding:10px 14px;font-size:0.76rem;color:#7a5c00;margin-bottom:1rem">
          📌 <strong>Note:</strong> Payment of <strong id="momoAmountNote">5,000 RWF</strong> will be sent to:<br>
          MTN MoMo: <strong>+250 78 933 601</strong> — JVN AI Education Services
        </div>

        <div style="display:flex;gap:10px">
          <button class="generate-btn" style="background:#eee;color:#555;flex:1" onclick="goSubStep(1)">← Back</button>
          <button class="generate-btn" style="flex:2" onclick="processMoMoPayment()">📱 Send MoMo Request</button>
        </div>
      </div>

      <!-- STEP 3: SUCCESS -->
      <div class="step-page" id="sub-step-3">
        <div class="success-screen">
          <div class="success-icon">✅</div>
          <h3>Payment Confirmed!</h3>
          <p>Your <strong id="successPlan">Pro</strong> subscription is now active.<br>Welcome to JVN AI — Rwanda's #1 CBC Teacher Assistant.</p>
          <div class="teacher-card" id="successCard">
            <div class="tc-label">Teacher Account</div>
            <div class="tc-value" id="successName">Teacher Name</div>
            <div class="tc-label" style="margin-top:8px">Subscription Plan</div>
            <div class="tc-value" id="successPlanText">Pro Plan</div>
            <div class="tc-label" style="margin-top:8px">Account ID</div>
            <div class="tc-id" id="successId">JVN-000000</div>
            <div class="tc-label" style="margin-top:8px">Valid Until</div>
            <div class="tc-value" id="successExpiry">—</div>
          </div>
          <p style="font-size:0.75rem;color:#aaa">A confirmation SMS has been sent to your MoMo number.</p>
          <button class="generate-btn" style="margin-top:1rem;width:100%" onclick="closeModal('subscribe');activateSubscription()">🎓 Start Using JVN AI</button>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- BODY -->
<div class="app-body">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-section-label">Grade Level</div>
    <div class="sidebar-grade-selector">
      <select id="gradeSelect" onchange="setGrade(this.value)">
        <option value="all">All Levels</option>
        <optgroup label="Lower Primary">
          <option value="P1">P1 – Year 1</option>
          <option value="P2">P2 – Year 2</option>
          <option value="P3">P3 – Year 3</option>
        </optgroup>
        <optgroup label="Upper Primary">
          <option value="P4">P4 – Year 4</option>
          <option value="P5">P5 – Year 5</option>
          <option value="P6">P6 – Year 6</option>
        </optgroup>
        <optgroup label="Lower Secondary (O-Level)">
          <option value="S1">S1</option>
          <option value="S2">S2</option>
          <option value="S3">S3</option>
        </optgroup>
        <optgroup label="Upper Secondary (A-Level)">
          <option value="S4">S4</option>
          <option value="S5">S5</option>
          <option value="S6">S6</option>
        </optgroup>
        <optgroup label="TVET">
          <option value="TVET-Y1">TVET Year 1</option>
          <option value="TVET-Y2">TVET Year 2</option>
          <option value="TVET-Y3">TVET Year 3</option>
        </optgroup>
      </select>
    </div>

    <div class="sidebar-section-label">Main Tools</div>
    <div class="nav-item active" onclick="showPanel('chat')" id="nav-chat">
      <span class="nav-icon">💬</span> AI Teaching Assistant
    </div>
    <div class="nav-item" onclick="showPanel('lesson')" id="nav-lesson">
      <span class="nav-icon">📋</span> Lesson Plan Builder
    </div>
    <div class="nav-item" onclick="showPanel('scheme')" id="nav-scheme">
      <span class="nav-icon">📅</span> Scheme of Work
    </div>
    <div class="nav-item" onclick="showPanel('unit')" id="nav-unit">
    </div>
    <div class="nav-item" onclick="showPanel('quiz')" id="nav-quiz">
      <span class="nav-icon">✏️</span> Quiz Generator
      <span class="nav-badge">New</span>
    </div>
    <div class="nav-item" onclick="showPanel('notes')" id="nav-notes">
      <span class="nav-icon">📝</span> Class Notes
    </div>
    <div class="nav-item" onclick="showPanel('slides')" id="nav-slides">
      <span class="nav-icon">🖥️</span> Slide Outlines
    </div>

    <div class="sidebar-section-label">Reference</div>
    <div class="nav-item" onclick="showPanel('subjects')" id="nav-subjects">
      <span class="nav-icon">🗂️</span> CBC Subjects
    </div>
    <div class="nav-item" onclick="showPanel('competencies')" id="nav-competencies">
      <span class="nav-icon">🎯</span> Key Competencies
    </div>

    <div class="sidebar-section-label">Language</div>
    <div class="nav-item" onclick="setLang('en')" id="nav-en">
      <span class="nav-icon">🇬🇧</span> English
    </div>
    <div class="nav-item" onclick="setLang('rw')" id="nav-rw">
      <span class="nav-icon">🇷🇼</span> Kinyarwanda
    </div>
    <div class="nav-item" onclick="setLang('fr')" id="nav-fr">
      <span class="nav-icon">🇫🇷</span> French
    </div>

    <div class="sidebar-section-label">Account</div>
    <div class="nav-item" onclick="openModal('login')">
      <span class="nav-icon">🔑</span> Login / Register
    </div>
    <div class="nav-item" onclick="openModal('subscribe')" style="color:var(--gold);font-weight:700">
      <span class="nav-icon">⭐</span> Subscribe — from 2,000 RWF
    </div>
  </aside>

  <!-- MAIN CONTENT -->
  <div class="main-content">

    <!-- CHAT PANEL (default) -->
    <div class="tool-panel active" id="panel-chat">
      <div class="tool-header">
        <h1>💬 AI Teaching Assistant</h1>
        <p>Ask anything about Rwanda's CBC curriculum – lesson plans, assessments, pedagogy, content, and more.</p>
      </div>
      <div class="chat-area" id="chatArea">
        <!-- Welcome message -->
        <div class="msg ai">
          <div class="msg-avatar">🤖</div>
          <div class="msg-bubble">
            <h3>Murakaza neza! Welcome to JVN AI 🇷🇼</h3>
            I'm your Rwanda CBC curriculum assistant. I can help you with:
            <ul>
              <li>📋 <strong>Lesson Plans</strong> aligned to CBC competencies</li>
              <li>📅 <strong>Schemes of Work</strong> for any term and subject</li>
              <li>✏️ <strong>Quizzes & Assessments</strong> matching CBC standards</li>
              <li>📝 <strong>Class Notes</strong> for students</li>
              <li>🖥️ <strong>Slide outlines</strong> for your lessons</li>
            </ul>
            <br>
            Select your grade level on the left, then ask me anything. What would you like to create today?
            <br>
            <button class="copy-btn" onclick="copyText(this)">📋 Copy</button>
          </div>
        </div>
      </div>
      <div class="input-bar">
        <div class="quick-prompts">
          <button class="qp-btn" onclick="quickPrompt('Create a lesson plan for Mathematics P4 on fractions')">📋 Lesson Plan</button>
          <button class="qp-btn" onclick="quickPrompt('Generate a Scheme of Work for S1 English Term 1')">📅 Scheme of Work</button>
          <button class="qp-btn" onclick="quickPrompt('Make a 10-question quiz on Science for P6')">✏️ Quiz</button>
          <button class="qp-btn" onclick="quickPrompt('Write class notes on photosynthesis for S2 Biology')">📝 Class Notes</button>
          <button class="qp-btn" onclick="quickPrompt('Create a unit plan for S3 History on colonialism')">📚 Unit Plan</button>
        </div>
        <div class="input-controls">
          <select class="ctrl-select" id="subjectCtrl">
            <option value="">Subject</option>
            <option>Mathematics</option>
            <option>English</option>
            <option>Kinyarwanda</option>
            <option>SET</option>
            <option>Social Studies</option>
            <option>ICT</option>
            <option>French</option>
            <option>Biology</option>
            <option>Chemistry</option>
            <option>Physics</option>
            <option>History</option>
            <option>Geography</option>
            <option>Economics</option>
            <option>Entrepreneurship</option>
            <option>Religious Education</option>
            <option>Physical Education</option>
            <option>Music</option>
            <option>Arts & Crafts</option>
          </select>
          <select class="ctrl-select" id="docTypeCtrl">
            <option value="">Document Type</option>
            <option>Lesson Plan</option>
            <option>Scheme of Work</option>
            <option>Quiz</option>
            <option>Class Notes</option>
            <option>Slide Outline</option>
            <option>Assessment Rubric</option>
          </select>
        </div>
        <div class="input-row">
          <div class="input-wrap">
            <textarea id="chatInput" placeholder="Ask anything about Rwanda's CBC curriculum…" rows="2" onkeydown="handleKey(event)"></textarea>
          </div>
          <button class="send-btn" onclick="sendMessage()" id="sendBtn">➤</button>
        </div>
      </div>
    </div>

    <!-- LESSON PLAN PANEL -->
    <div class="tool-panel" id="panel-lesson">
      <div class="tool-header">
        <h1>📋 Lesson Plan Builder</h1>
        <p>Generate CBC-aligned lesson plans for any grade and subject.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          <h2>📋 Build a Lesson Plan</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="lp-grade">
                <option>P1</option><option>P2</option><option>P3</option>
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="lp-subject">
                <option>Mathematics</option><option>English</option>
                <option>Kinyarwanda</option><option>Science</option>
                <option>Social Studies</option><option>ICT</option>
                <option>French</option><option>Biology</option>
                <option>Chemistry</option><option>Physics</option>
                <option>History</option><option>Geography</option>
                <option>Economics</option><option>Entrepreneurship</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Topic / Unit</label>
            <input type="text" id="lp-topic" placeholder="e.g. Addition and Subtraction, The Water Cycle, Colonial History…">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Duration</label>
              <select id="lp-duration">
                <option>40 minutes</option>
                <option>60 minutes</option>
                <option>80 minutes</option>
                
              </select>
            </div>
            <div class="form-group">
              <label>Term</label>
              <select id="lp-term">
                <option>Term 1</option>
                <option>Term 2</option>
                <option>Term 3</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Specific Objectives (optional)</label>
            <textarea rows="2" id="lp-objectives" placeholder="What specific learning outcomes should this lesson achieve?"></textarea>
          </div>
          <button class="generate-btn" onclick="generateFromForm('lesson')">✨ Generate Lesson Plan</button>
        </div>
      </div>
    </div>

    <!-- SCHEME OF WORK PANEL -->
    <div class="tool-panel" id="panel-scheme">
      <div class="tool-header">
        <h1>📅 Scheme of Work</h1>
        <p>Generate full term schemes of work aligned to Rwanda CBC syllabus.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          <h2>📅 Build a Scheme of Work</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="sw-grade">
                <option>P1</option><option>P2</option><option>P3</option>
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="sw-subject">
                <option>Mathematics</option><option>English</option>
                <option>Kinyarwanda</option><option>Science</option>
                <option>Social Studies</option><option>ICT</option>
                <option>Biology</option><option>Chemistry</option>
                <option>Physics</option><option>History</option>
                <option>Geography</option><option>Economics</option>
              </select>
            </div>
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Term</label>
              <select id="sw-term">
                <option>Term 1</option><option>Term 2</option><option>Term 3</option>
              </select>
            </div>
            <div class="form-group">
              <label>Number of Weeks</label>
              <select id="sw-weeks">
                <option>10</option><option>11</option><option>12</option><option>13</option><option>14</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Periods per Week</label>
            <select id="sw-periods">
              <option>3</option><option>4</option><option>5</option><option>6</option>
            </select>
          </div>
          <button class="generate-btn" onclick="generateFromForm('scheme')">✨ Generate Scheme of Work</button>
        </div>
      </div>
    </div>

    <!-- UNIT PLAN PANEL -->
    <div class="tool-panel" id="panel-unit">
      <div class="tool-header">
        <h1>📚 Unit Plan</h1>
        <p>Build comprehensive unit plans with learning outcomes and activities.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="up-grade">
                <option>P1</option><option>P2</option><option>P3</option>
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="up-subject">
                <option>Mathematics</option><option>English</option>
                <option>Kinyarwanda</option><option>Science</option>
                <option>Social Studies</option><option>ICT</option>
                <option>Biology</option><option>Chemistry</option>
                <option>Physics</option><option>History</option>
                <option>Geography</option><option>Economics</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Unit Title</label>
            <input type="text" id="up-title" placeholder="e.g. Living Things, Algebraic Expressions, The Great Lakes Region…">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Duration (weeks)</label>
              <select id="up-weeks">
                <option>2</option><option>3</option><option>4</option><option>5</option><option>6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Assessment Type</label>
              <select id="up-assess">
                <option>Formative + Summative</option>
                <option>Formative only</option>
                <option>Summative only</option>
                <option>Portfolio</option>
                <option>Project-based</option>
              </select>
            </div>
          </div>
          <button class="generate-btn" onclick="generateFromForm('unit')">✨ Generate Unit Plan</button>
        </div>
      </div>
    </div>

    <!-- QUIZ PANEL -->
    <div class="tool-panel" id="panel-quiz">
      <div class="tool-header">
        <h1>✏️ Quiz Generator</h1>
        <p>Create CBC-aligned assessments, tests, and quizzes for any subject.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          <h2>✏️ Generate a Quiz</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="qz-grade">
                <option>P1</option><option>P2</option><option>P3</option>
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="qz-subject">
                <option>Mathematics</option><option>English</option>
                <option>Kinyarwanda</option><option>Science</option>
                <option>Social Studies</option><option>ICT</option>
                <option>Biology</option><option>Chemistry</option>
                <option>Physics</option><option>History</option>
                <option>Geography</option><option>Economics</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Topic</label>
            <input type="text" id="qz-topic" placeholder="e.g. Fractions, Photosynthesis, World War II…">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Number of Questions</label>
              <select id="qz-num">
                <option>5</option><option>10</option><option>15</option><option>20</option><option>25</option>
              </select>
            </div>
            <div class="form-group">
              <label>Question Types</label>
              <select id="qz-type">
                <option>Mixed (MCQ + Short Answer)</option>
                <option>Multiple Choice only</option>
                <option>Short Answer only</option>
                <option>True/False</option>
                <option>Fill in the Blanks</option>
                <option>Essay Questions</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Difficulty Level</label>
            <select id="qz-diff">
              <option>Mixed (Easy, Medium, Hard)</option>
              <option>Easy (Recall & Knowledge)</option>
              <option>Medium (Understanding & Application)</option>
              <option>Hard (Analysis & Evaluation)</option>
            </select>
          </div>
          <button class="generate-btn" onclick="generateFromForm('quiz')">✨ Generate Quiz</button>
        </div>
      </div>
    </div>

    <!-- NOTES PANEL -->
    <div class="tool-panel" id="panel-notes">
      <div class="tool-header">
        <h1>📝 Class Notes</h1>
        <p>Generate clear, student-friendly class notes for any topic.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          <h2>📝 Generate Class Notes</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="cn-grade">
                <option>P1</option><option>P2</option><option>P3</option>
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="cn-subject">
                <option>Mathematics</option><option>English</option>
                <option>Kinyarwanda</option><option>Science</option>
                <option>Social Studies</option><option>ICT</option>
                <option>Biology</option><option>Chemistry</option>
                <option>Physics</option><option>History</option>
                <option>Geography</option><option>Economics</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Topic</label>
            <input type="text" id="cn-topic" placeholder="e.g. The Water Cycle, Multiplication of Decimals, The Cell…">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Level of Detail</label>
              <select id="cn-detail">
                <option>Summary notes</option>
                <option>Detailed notes with examples</option>
                <option>Full comprehensive notes</option>
              </select>
            </div>
            <div class="form-group">
              <label>Language</label>
              <select id="cn-lang">
                <option>English</option>
                <option>Kinyarwanda</option>
                <option>French</option>
              </select>
            </div>
          </div>
          <button class="generate-btn" onclick="generateFromForm('notes')">✨ Generate Class Notes</button>
        </div>
      </div>
    </div>

    <!-- SLIDES PANEL -->
    <div class="tool-panel" id="panel-slides">
      <div class="tool-header">
        <h1>🖥️ Slide Outlines</h1>
        <p>Create structured lesson slide outlines with talking points.</p>
      </div>
      <div class="quiz-builder">
        <div class="form-card">
          <h2>🖥️ Generate Slide Outline</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Grade Level</label>
              <select id="sl-grade">
                <option>P4</option><option>P5</option><option>P6</option>
                <option>S1</option><option>S2</option><option>S3</option>
                <option>S4</option><option>S5</option><option>S6</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <select id="sl-subject">
                <option>Mathematics</option><option>English</option>
                <option>Science</option><option>Social Studies</option>
                <option>ICT</option><option>Biology</option>
                <option>Chemistry</option><option>Physics</option>
                <option>History</option><option>Geography</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Lesson Topic</label>
            <input type="text" id="sl-topic" placeholder="e.g. Introduction to Algebra, The Human Digestive System…">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Number of Slides</label>
              <select id="sl-num">
                <option>8</option><option>10</option><option>12</option><option>15</option><option>20</option>
              </select>
            </div>
            <div class="form-group">
              <label>Style</label>
              <select id="sl-style">
                <option>Teaching presentation</option>
                <option>Student presentation</option>
                <option>Interactive lesson</option>
                <option>Review/Revision</option>
              </select>
            </div>
          </div>
          <button class="generate-btn" onclick="generateFromForm('slides')">✨ Generate Slide Outline</button>
        </div>
      </div>
    </div>

    <!-- SUBJECTS PANEL -->
    <div class="tool-panel" id="panel-subjects">
      <div class="tool-header">
        <h1>🗂️ CBC Subjects by Level</h1>
        <p>Click any subject to ask the AI about it for your selected grade.</p>
      </div>
      <div class="subjects-panel">
        <div class="subject-group">
          <h2>📚 Lower Primary (P1–P3)</h2>
          <div class="subject-tags">
            <span class="subject-tag" onclick="subjectQuickChat('Mathematics', 'P1-P3')">Mathematics</span>
            <span class="subject-tag" onclick="subjectQuickChat('Kinyarwanda', 'P1-P3')">Kinyarwanda</span>
            <span class="subject-tag" onclick="subjectQuickChat('English', 'P1-P3')">English</span>
            <span class="subject-tag" onclick="subjectQuickChat('Social Studies', 'P1-P3')">Social Studies</span>
            <span class="subject-tag" onclick="subjectQuickChat('Science and Elementary Technology', 'P1-P3')">Science & Elementary Technology</span>
            <span class="subject-tag" onclick="subjectQuickChat('Creative Arts', 'P1-P3')">Creative Arts</span>
            <span class="subject-tag" onclick="subjectQuickChat('Physical Education', 'P1-P3')">Physical Education</span>
            <span class="subject-tag" onclick="subjectQuickChat('Religious Education', 'P1-P3')">Religious Education</span>
          </div>
        </div>
        <div class="subject-group">
          <h2>📚 Upper Primary (P4–P6)</h2>
          <div class="subject-tags">
            <span class="subject-tag" onclick="subjectQuickChat('Mathematics', 'P4-P6')">Mathematics</span>
            <span class="subject-tag" onclick="subjectQuickChat('English', 'P4-P6')">English</span>
            <span class="subject-tag" onclick="subjectQuickChat('Kinyarwanda', 'P4-P6')">Kinyarwanda</span>
            <span class="subject-tag" onclick="subjectQuickChat('French', 'P4-P6')">French</span>
            <span class="subject-tag" onclick="subjectQuickChat('Science and Elementary Technology', 'P4-P6')">Science & Technology</span>
            <span class="subject-tag" onclick="subjectQuickChat('Social Studies', 'P4-P6')">Social Studies</span>
            <span class="subject-tag" onclick="subjectQuickChat('ICT', 'P4-P6')">ICT</span>
            <span class="subject-tag" onclick="subjectQuickChat('Physical Education', 'P4-P6')">Physical Education</span>
            <span class="subject-tag" onclick="subjectQuickChat('Religious Education', 'P4-P6')">Religious Education</span>
          </div>
        </div>
        <div class="subject-group">
          <h2>📚 O-Level (S1–S3)</h2>
          <div class="subject-tags">
            <span class="subject-tag" onclick="subjectQuickChat('Mathematics', 'S1-S3')">Mathematics</span>
            <span class="subject-tag" onclick="subjectQuickChat('English', 'S1-S3')">English</span>
            <span class="subject-tag" onclick="subjectQuickChat('Kinyarwanda', 'S1-S3')">Kinyarwanda</span>
            <span class="subject-tag" onclick="subjectQuickChat('French', 'S1-S3')">French</span>
            <span class="subject-tag" onclick="subjectQuickChat('Biology', 'S1-S3')">Biology</span>
            <span class="subject-tag" onclick="subjectQuickChat('Chemistry', 'S1-S3')">Chemistry</span>
            <span class="subject-tag" onclick="subjectQuickChat('Physics', 'S1-S3')">Physics</span>
            <span class="subject-tag" onclick="subjectQuickChat('History', 'S1-S3')">History</span>
            <span class="subject-tag" onclick="subjectQuickChat('Geography', 'S1-S3')">Geography</span>
            <span class="subject-tag" onclick="subjectQuickChat('Economics', 'S1-S3')">Economics</span>
            <span class="subject-tag" onclick="subjectQuickChat('ICT', 'S1-S3')">ICT</span>
            <span class="subject-tag" onclick="subjectQuickChat('Entrepreneurship', 'S1-S3')">Entrepreneurship</span>
            <span class="subject-tag" onclick="subjectQuickChat('Physical Education', 'S1-S3')">Physical Education</span>
            <span class="subject-tag" onclick="subjectQuickChat('Religious Education', 'S1-S3')">Religious Education</span>
          </div>
        </div>
        <div class="subject-group">
          <h2>📚 A-Level (S4–S6)</h2>
          <div class="subject-tags">
            <span class="subject-tag" onclick="subjectQuickChat('Mathematics', 'S4-S6')">Mathematics</span>
            <span class="subject-tag" onclick="subjectQuickChat('English', 'S4-S6')">English</span>
            <span class="subject-tag" onclick="subjectQuickChat('Biology', 'S4-S6')">Biology</span>
            <span class="subject-tag" onclick="subjectQuickChat('Chemistry', 'S4-S6')">Chemistry</span>
            <span class="subject-tag" onclick="subjectQuickChat('Physics', 'S4-S6')">Physics</span>
            <span class="subject-tag" onclick="subjectQuickChat('History', 'S4-S6')">History</span>
            <span class="subject-tag" onclick="subjectQuickChat('Geography', 'S4-S6')">Geography</span>
            <span class="subject-tag" onclick="subjectQuickChat('Economics', 'S4-S6')">Economics</span>
            <span class="subject-tag" onclick="subjectQuickChat('Accounting', 'S4-S6')">Accounting</span>
            <span class="subject-tag" onclick="subjectQuickChat('Computer Science', 'S4-S6')">Computer Science</span>
            <span class="subject-tag" onclick="subjectQuickChat('Literature in English', 'S4-S6')">Literature in English</span>
            <span class="subject-tag" onclick="subjectQuickChat('Entrepreneurship', 'S4-S6')">Entrepreneurship</span>
          </div>
        </div>
      </div>
    </div>

    <!-- COMPETENCIES PANEL -->
    <div class="tool-panel" id="panel-competencies">
      <div class="tool-header">
        <h1>🎯 Rwanda CBC Key Competencies</h1>
        <p>The seven core competencies of Rwanda's Competency-Based Curriculum.</p>
      </div>
      <div class="resource-grid">
        <div class="resource-card" onclick="competencyChat('Literacy')">
          <div class="rc-icon">📖</div>
          <h3>Literacy</h3>
          <p>Reading, writing, and communicating effectively in Kinyarwanda, English, and French.</p>
          <div class="rc-meta"><span class="tag">Language</span><span class="tag">All Levels</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Numeracy')">
          <div class="rc-icon">🔢</div>
          <h3>Numeracy</h3>
          <p>Mathematical thinking, problem-solving, and applying numbers in real-life contexts.</p>
          <div class="rc-meta"><span class="tag">Mathematics</span><span class="tag">STEM</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('ICT and Digital Literacy')">
          <div class="rc-icon">💻</div>
          <h3>ICT & Digital Literacy</h3>
          <p>Using technology responsibly and effectively to access, create, and share information.</p>
          <div class="rc-meta"><span class="tag">Technology</span><span class="tag">21st Century</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Critical Thinking and Problem Solving')">
          <div class="rc-icon">🧠</div>
          <h3>Critical Thinking & Problem Solving</h3>
          <p>Analyzing situations, evaluating evidence, and solving real-world problems creatively.</p>
          <div class="rc-meta"><span class="tag">Higher Order</span><span class="tag">Core</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Creativity and Innovation')">
          <div class="rc-icon">💡</div>
          <h3>Creativity & Innovation</h3>
          <p>Generating new ideas, creating original work, and finding innovative solutions.</p>
          <div class="rc-meta"><span class="tag">Creative</span><span class="tag">Entrepreneurship</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Communication')">
          <div class="rc-icon">🗣️</div>
          <h3>Communication</h3>
          <p>Expressing ideas clearly through speaking, writing, and multimodal communication.</p>
          <div class="rc-meta"><span class="tag">Language</span><span class="tag">Social</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Cooperation and Teamwork')">
          <div class="rc-icon">🤝</div>
          <h3>Cooperation & Teamwork</h3>
          <p>Working collaboratively, respecting others, and contributing to group success.</p>
          <div class="rc-meta"><span class="tag">Social</span><span class="tag">Civic</span></div>
        </div>
        <div class="resource-card" onclick="competencyChat('Personal Development and Self-Reliance')">
          <div class="rc-icon">🌱</div>
          <h3>Personal Development</h3>
          <p>Self-management, life skills, and developing the values of Agaciro (dignity) and Ndi Umunyarwanda.</p>
          <div class="rc-meta"><span class="tag">Values</span><span class="tag">Identity</span></div>
        </div>
      </div>
    </div>

  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  // ── STATE ──
  let currentGrade = 'all';
  let currentLang = 'en';
  const API_URL = "https://api.anthropic.com/v1/messages";

  // ── CBC SYSTEM PROMPT ──
  const CBC_SYSTEM = `You are JVN AI, an expert Rwanda Competency-Based Curriculum (CBC) teaching assistant.

You have deep knowledge of:
- Rwanda's CBC framework across all levels: Lower Primary (P1-P3), Upper Primary (P4-P6), O-Level (S1-S3), A-Level (S4-S6), and TVET
- All CBC subjects: Mathematics, English, Kinyarwanda, French, Science & Elementary Technology, Social Studies, ICT, Biology, Chemistry, Physics, History, Geography, Economics, Entrepreneurship, Accounting, Physical Education, Religious Education, Creative Arts, Music
- Rwanda's 7 key competencies: Literacy, Numeracy, ICT & Digital Literacy, Critical Thinking & Problem Solving, Creativity & Innovation, Communication, Cooperation & Teamwork, Personal Development & Self-Reliance
- Rwanda Education Board (REB) curriculum standards and guidelines
- CBC pedagogical approaches: learner-centered learning, competency-based assessment, formative and summative assessment
- Rwanda national values: Ndi Umunyarwanda, Agaciro, Unity and Reconciliation
- Bloom's Taxonomy applied to CBC learning outcomes
- CBC assessment types: class activities, group work, assignments, tests, national exams

When generating documents, format them professionally using:
- Proper CBC terminology (Learning Objectives → Learning Outcomes, etc.)
- Aligned competencies from the 7 key competencies
- SMART learning outcomes
- CBC lesson plan sections: Introduction/Background, Learning Resources, Prerequisites, Learning Objectives, Activities (Introduction, Development, Conclusion), Assessment, Teacher's notes
- Scheme of Work table format: Week | Topic | Sub-topic | Learning Outcomes | Teaching/Learning Activities | Resources | Assessment
- Rwanda's grading scale and assessment standards

Always make content:
1. Culturally relevant to Rwanda and East African context
2. Aligned to CBC's competency-based approach
3. Inclusive and gender-sensitive
4. Practical with local examples (use Rwandan names, places, currencies in FRW)
5. Professional and ready to use in class

Respond in the language requested (English, Kinyarwanda, or French).`;

  // ── NAVIGATION ──
  function showPanel(name) {
    document.querySelectorAll('.tool-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
    document.getElementById('panel-' + name).classList.add('active');
    document.getElementById('nav-' + name) && document.getElementById('nav-' + name).classList.add('active');
  }

  function setGrade(val) {
    currentGrade = val;
    document.getElementById('headerGrade').textContent = val === 'all' ? 'All Levels' : val;
  }

  function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('[id^="nav-en"], [id^="nav-rw"], [id^="nav-fr"]').forEach(el => el.classList.remove('active'));
    document.getElementById('nav-' + lang).classList.add('active');
    showToast('Language set to ' + {en: 'English', rw: 'Kinyarwanda', fr: 'French'}[lang]);
  }

  // ── MESSAGING ──
  function handleKey(e) {
    if (e.key === 'Enter' && !e.shiftKey) {
      e.preventDefault();
      sendMessage();
    }
  }

  function quickPrompt(text) {
    document.getElementById('chatInput').value = text;
    showPanel('chat');
    sendMessage();
  }

  function subjectQuickChat(subject, grade) {
    showPanel('chat');
    const prompt = `Tell me about ${subject} for ${grade} in Rwanda's CBC curriculum. What are the main topics, learning outcomes, and suggested teaching approaches? I am JVN AI and I'm here to help.`;
    document.getElementById('chatInput').value = prompt;
    sendMessage();
  }

  function competencyChat(competency) {
    showPanel('chat');
    const grade = currentGrade !== 'all' ? ` for ${currentGrade}` : '';
    const prompt = `How can I integrate the "${competency}" competency into my lessons${grade}? Give me practical examples and activities.`;
    document.getElementById('chatInput').value = prompt;
    sendMessage();
  }

  function generateFromForm(type) {
    let prompt = '';
    const grade = document.getElementById(type[0] + type[1] + '-grade')?.value ||
                  document.getElementById('qz-grade')?.value ||
                  document.getElementById('lp-grade')?.value || currentGrade;

    if (type === 'lesson') {
      const g = document.getElementById('lp-grade').value;
      const s = document.getElementById('lp-subject').value;
      const t = document.getElementById('lp-topic').value || 'Introduction to the topic';
      const d = document.getElementById('lp-duration').value;
      const term = document.getElementById('lp-term').value;
      const obj = document.getElementById('lp-objectives').value;
      prompt = `Create a complete CBC lesson plan for:\n- Grade: ${g}\n- Subject: ${s}\n- Topic: ${t}\n- Duration: ${d}\n- Term: ${term}\n${obj ? '- Specific objectives: ' + obj : ''}\n\nInclude all standard CBC sections: school info header, learning outcomes, key competencies, prerequisite knowledge, teaching/learning materials, introduction (10%), development (80%), conclusion (10%), formative assessment, teacher's self-evaluation, and any notes.`;
    } else if (type === 'scheme') {
      const g = document.getElementById('sw-grade').value;
      const s = document.getElementById('sw-subject').value;
      const term = document.getElementById('sw-term').value;
      const weeks = document.getElementById('sw-weeks').value;
      const periods = document.getElementById('sw-periods').value;
      prompt = `Create a complete Scheme of Work for:\n- Grade: ${g}\n- Subject: ${s}\n- Term: ${term}\n- Number of weeks: ${weeks}\n- Periods per week: ${periods}\n\nFormat as a detailed table with columns: Week | Period | Topic | Sub-topic | Learning Outcomes | Teaching/Learning Activities | Resources | Assessment Method. Cover the full term systematically.`;
    } else if (type === 'unit') {
      const g = document.getElementById('up-grade').value;
      const s = document.getElementById('up-subject').value;
      const t = document.getElementById('up-title').value || 'Selected Unit';
      const weeks = document.getElementById('up-weeks').value;
      const assess = document.getElementById('up-assess').value;
      prompt = `Create a comprehensive Unit Plan for:\n- Grade: ${g}\n- Subject: ${s}\n- Unit Title: ${t}\n- Duration: ${weeks} weeks\n- Assessment approach: ${assess}\n\nInclude: Unit overview, essential questions, enduring understandings, knowledge & skills, key competencies addressed, weekly breakdown with lessons, formative & summative assessment tasks, resources list, and differentiation strategies.`;
    } else if (type === 'quiz') {
      const g = document.getElementById('qz-grade').value;
      const s = document.getElementById('qz-subject').value;
      const t = document.getElementById('qz-topic').value || 'General topic';
      const num = document.getElementById('qz-num').value;
      const qtype = document.getElementById('qz-type').value;
      const diff = document.getElementById('qz-diff').value;
      prompt = `Create a ${num}-question quiz/assessment for:\n- Grade: ${g}\n- Subject: ${s}\n- Topic: ${t}\n- Question types: ${qtype}\n- Difficulty: ${diff}\n\nFor each question include the question, answer options (if MCQ), correct answer, and marks. End with a marking guide/answer key. Align to CBC competencies.`;
    } else if (type === 'notes') {
      const g = document.getElementById('cn-grade').value;
      const s = document.getElementById('cn-subject').value;
      const t = document.getElementById('cn-topic').value || 'Selected topic';
      const detail = document.getElementById('cn-detail').value;
      const lang = document.getElementById('cn-lang').value;
      prompt = `Create ${detail} for students on:\n- Grade: ${g}\n- Subject: ${s}\n- Topic: ${t}\n- Language: ${lang}\n\nMake notes clear, well-structured with headings, examples relevant to Rwanda, diagrams (described textually), key terms defined, summary points, and review questions at the end. Student-friendly and age-appropriate.`;
    } else if (type === 'slides') {
      const g = document.getElementById('sl-grade').value;
      const s = document.getElementById('sl-subject').value;
      const t = document.getElementById('sl-topic').value || 'Selected topic';
      const num = document.getElementById('sl-num').value;
      const style = document.getElementById('sl-style').value;
      prompt = `Create a ${num}-slide outline for a ${style} on:\n- Grade: ${g}\n- Subject: ${s}\n- Topic: ${t}\n\nFor each slide provide: Slide number, Title, 3-5 bullet points/key content, teaching notes/talking points, and any suggested visuals or activities. First slide = title slide, last slide = summary/questions.`;
    }

    const gradeCtx = currentGrade !== 'all' ? ` (Grade context: ${currentGrade})` : '';
    document.getElementById('chatInput').value = prompt + gradeCtx;
    showPanel('chat');
    sendMessage();
  }

  async function sendMessage() {
    const input = document.getElementById('chatInput');
    const text = input.value.trim();
    if (!text) return;

    const subject = document.getElementById('subjectCtrl')?.value;
    const docType = document.getElementById('docTypeCtrl')?.value;

    let fullText = text;
    if (subject || docType || currentGrade !== 'all') {
      const ctx = [];
      if (currentGrade !== 'all') ctx.push(`Grade: ${currentGrade}`);
      if (subject) ctx.push(`Subject: ${subject}`);
      if (docType) ctx.push(`Document type: ${docType}`);
      if (ctx.length) fullText = `[Context: ${ctx.join(', ')}]\n\n${text}`;
    }

    const langInstruction = currentLang === 'rw' ? ' Please respond in Kinyarwanda.' : currentLang === 'fr' ? ' Please respond in French.' : '';
    if (langInstruction) fullText += langInstruction;

    addMsg('user', text);
    input.value = '';
    input.style.height = 'auto';

    const typing = addTyping();
    setLoading(true);

    try {
      const res = await fetch(API_URL, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          model: 'claude-sonnet-4-20250514',
          max_tokens: 2000,
          system: CBC_SYSTEM,
          messages: [{ role: 'user', content: fullText }]
        })
      });

      const data = await res.json();
      removeTyping(typing);

      if (data.content && data.content[0]) {
        const reply = data.content[0].text;
        addMsg('ai', formatReply(reply));
      } else if (data.error) {
        addMsg('ai', `⚠️ API error: ${data.error.message || 'Something went wrong. Please try again.'}`);
      }
    } catch (err) {
      removeTyping(typing);
      addMsg('ai', `⚠️ Connection error. Please check your network and try again.\n\nError: ${err.message}`);
    }

    setLoading(false);
  }

  function formatReply(text) {
    // Convert markdown-like formatting to HTML
    text = text
      .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
      .replace(/\*(.*?)\*/g, '<em>$1</em>')
      .replace(/`(.*?)`/g, '<code style="background:#f0f0f0;padding:1px 5px;border-radius:4px;font-size:0.85em">$1</code>')
      .replace(/^#{3}\s(.+)/gm, '<h4 style="margin:12px 0 6px;color:#0a7c4f;font-size:0.92rem">$1</h4>')
      .replace(/^#{2}\s(.+)/gm, '<h3 style="margin:14px 0 8px;color:#0a7c4f;font-size:1rem">$1</h3>')
      .replace(/^#{1}\s(.+)/gm, '<h3 style="margin:16px 0 8px;color:#0a7c4f;font-size:1.05rem">$1</h3>')
      .replace(/^[-•]\s(.+)/gm, '<li>$1</li>')
      .replace(/^\d+\.\s(.+)/gm, '<li>$1</li>')
      .replace(/(<li>.*<\/li>)/gs, '<ul style="padding-left:1.2rem;margin:6px 0">$1</ul>')
      .replace(/\n\n/g, '<br><br>')
      .replace(/\n/g, '<br>');

    // Wrap in div with copy button
    return `<div>${text}</div><button class="copy-btn" onclick="copyText(this)">📋 Copy</button>`;
  }

  function addMsg(type, html) {
    const area = document.getElementById('chatArea');
    const div = document.createElement('div');
    div.className = `msg ${type}`;

    const avatarDiv = document.createElement('div');
    avatarDiv.className = 'msg-avatar';
    avatarDiv.textContent = type === 'ai' ? '🤖' : 'T';

    const bubble = document.createElement('div');
    bubble.className = 'msg-bubble';
    bubble.innerHTML = html;

    div.appendChild(avatarDiv);
    div.appendChild(bubble);
    area.appendChild(div);
    area.scrollTop = area.scrollHeight;
    return div;
  }

  function addTyping() {
    const area = document.getElementById('chatArea');
    const div = document.createElement('div');
    div.className = 'typing-indicator';
    div.innerHTML = `
      <div class="msg-avatar" style="background:var(--green);border-radius:50%;width:36px;height:36px;display:flex;align-items:center;justify-content:center;font-size:1.1rem">🤖</div>
      <div class="typing-dots">
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
      </div>`;
    area.appendChild(div);
    area.scrollTop = area.scrollHeight;
    return div;
  }

  function removeTyping(el) { el && el.remove(); }

  function setLoading(state) {
    document.getElementById('loadingBar').classList.toggle('active', state);
    document.getElementById('sendBtn').disabled = state;
  }

  function copyText(btn) {
    const bubble = btn.closest('.msg-bubble');
    const text = bubble.innerText.replace('📋 Copy', '').trim();
    navigator.clipboard.writeText(text).then(() => showToast('✅ Copied to clipboard!'));
  }

  function showToast(msg) {
    const toast = document.getElementById('toast');
    toast.textContent = msg;
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 2500);
  }

  // Auto-resize textarea
  document.addEventListener('DOMContentLoaded', () => {
    const ta = document.getElementById('chatInput');
    if (ta) {
      ta.addEventListener('input', function() {
        this.style.height = 'auto';
        this.style.height = Math.min(this.scrollHeight, 150) + 'px';
      });
    }
  });
  // ══════════════════════════════════════════
  // REGISTRATION, LOGIN & SUBSCRIPTION LOGIC
  // ══════════════════════════════════════════

  let currentUser = null;
  let selectedPlan = { name: 'Pro', price: 5000 };
  let currentSubStep = 1;

  // ── MODAL CONTROLS ──
  function openModal(id) {
    document.getElementById('modal-' + id).classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function closeModal(id) {
    document.getElementById('modal-' + id).classList.remove('open');
    document.body.style.overflow = '';
  }

  // Close on overlay click
  document.querySelectorAll('.modal-overlay').forEach(overlay => {
    overlay.addEventListener('click', function(e) {
      if (e.target === this) {
        this.classList.remove('open');
        document.body.style.overflow = '';
      }
    });
  });

  // ── AUTH TABS ──
  function switchAuthTab(formId) {
    document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.auth-form').forEach(f => f.classList.remove('active'));
    document.getElementById(formId).classList.add('active');
    const idx = formId === 'login-form' ? 0 : 1;
    document.querySelectorAll('.auth-tab')[idx].classList.add('active');
  }

  // ── REGISTER TEACHER ──
  function registerTeacher() {
    const fn  = document.getElementById('reg-firstname').value.trim();
    const ln  = document.getElementById('reg-lastname').value.trim();
    const em  = document.getElementById('reg-email').value.trim();
    const ph  = document.getElementById('reg-phone').value.trim();
    const sc  = document.getElementById('reg-school').value.trim();
    const di  = document.getElementById('reg-district').value;
    const sub = document.getElementById('reg-subject').value;
    const gl  = document.getElementById('reg-gradelevel').value;
    const pw  = document.getElementById('reg-password').value;

    if (!fn || !ln || !em || !ph || !sc || !di || !pw) {
      showToast('⚠️ Please fill in all required fields'); return;
    }
    if (!em.includes('@')) {
      showToast('⚠️ Please enter a valid email address'); return;
    }
    if (pw.length < 6) {
      showToast('⚠️ Password must be at least 6 characters'); return;
    }

    const teacherId = 'JVN-' + Math.floor(100000 + Math.random() * 900000);
    const teacher = {
      id: teacherId,
      name: fn + ' ' + ln,
      firstName: fn,
      email: em,
      phone: ph,
      school: sc,
      district: di,
      subject: sub,
      gradeLevel: gl,
      plan: 'Free',
      registeredAt: new Date().toISOString()
    };

    // Save to localStorage
    localStorage.setItem('jvnai_user', JSON.stringify(teacher));
    currentUser = teacher;

    closeModal('login');
    updateTeacherBar(teacher);
    showToast('🎉 Welcome to JVN AI, ' + fn + '! Account created successfully.');

    // Prompt to subscribe
    setTimeout(() => openModal('subscribe'), 1200);
  }

  // ── LOGIN TEACHER ──
  function loginTeacher() {
    const em = document.getElementById('login-email').value.trim();
    const pw = document.getElementById('login-password').value;

    if (!em || !pw) {
      showToast('⚠️ Please enter your email and password'); return;
    }

    const stored = localStorage.getItem('jvnai_user');
    if (stored) {
      const teacher = JSON.parse(stored);
      if (teacher.email === em) {
        currentUser = teacher;
        closeModal('login');
        updateTeacherBar(teacher);
        showToast('🎉 Welcome back, ' + teacher.name.split(' ')[0] + '!');
        return;
      }
    }

    // Demo/test login
    const demoTeacher = {
      id: 'JVN-DEMO01',
      name: em.split('@')[0].replace(/[._]/g, ' '),
      email: em,
      phone: '0780000000',
      school: 'Demo School',
      district: 'Gasabo',
      subject: 'Multiple subjects',
      gradeLevel: 'Multiple levels',
      plan: 'Free'
    };
    localStorage.setItem('jvnai_user', JSON.stringify(demoTeacher));
    currentUser = demoTeacher;
    closeModal('login');
    updateTeacherBar(demoTeacher);
    showToast('✅ Logged in successfully!');
  }

  // ── LOGOUT ──
  function logoutTeacher() {
    currentUser = null;
    document.getElementById('teacherBar').classList.remove('visible');
    showToast('👋 Logged out successfully');
  }

  // ── UPDATE TEACHER BAR ──
  function updateTeacherBar(teacher) {
    document.getElementById('tbName').textContent = teacher.name;
    document.getElementById('tbSchool').textContent = teacher.school;
    document.getElementById('tbGrade').textContent = teacher.gradeLevel || 'All levels';
    document.getElementById('tbPlan').textContent = teacher.plan || 'Free';
    document.getElementById('teacherBar').classList.add('visible');
    document.getElementById('userAvatar').textContent = teacher.name.charAt(0).toUpperCase();
  }

  // ── PLAN SELECTION ──
  function selectPlan(name, price) {
    selectedPlan = { name, price };
    document.querySelectorAll('.plan-card').forEach(c => c.classList.remove('selected'));
    document.getElementById('plan-' + name).classList.add('selected');
  }

  // ── SUBSCRIPTION STEPS ──
  function goSubStep(step) {
    document.querySelectorAll('.step-page').forEach(p => p.classList.remove('active'));
    document.getElementById('sub-step-' + step).classList.add('active');
    currentSubStep = step;

    // Update step dots
    for (let i = 1; i <= 3; i++) {
      const dot = document.getElementById('sdot-' + i);
      dot.classList.remove('active', 'done');
      if (i < step) dot.classList.add('done');
      else if (i === step) dot.classList.add('active');
    }
    for (let i = 1; i <= 2; i++) {
      const line = document.getElementById('sline-' + i);
      line.classList.toggle('done', i < step);
    }

    // Update MoMo amounts
    if (step === 2) {
      const fmt = selectedPlan.price.toLocaleString();
      document.getElementById('momoAmount').textContent = fmt + ' RWF';
      document.getElementById('momoplan').textContent = selectedPlan.name + ' Plan';
      document.getElementById('momoAmountNote').textContent = fmt + ' RWF';
    }
  }

  // ══════════════════════════════════════════
  // MTN MOMO COLLECTIONS API — REAL INTEGRATION
  // ══════════════════════════════════════════
  //
  // HOW TO GO LIVE:
  //   1. Register at https://momoapi.mtn.co.rw and subscribe to "Collections"
  //   2. Get your Subscription Key, API User ID, and API Key from the portal
  //   3. Replace the placeholders below with your real credentials
  //   4. Change MOMO_ENV to 'mtnrwanda' and MOMO_BASE_URL to the live URL
  //   5. Because browsers block cross-origin requests, you MUST proxy the API
  //      calls through a small backend (Node/Python/PHP) — see BACKEND PROXY note below.
  //
  // BACKEND PROXY NOTE:
  //   MTN MoMo API requires server-side calls (CORS + secret keys must stay private).
  //   Deploy a tiny proxy endpoint, e.g.:
  //     POST /api/momo/request-payment  → calls MTN Collections requesttopay
  //     GET  /api/momo/status/:ref      → checks payment status
  //   Then update MOMO_PROXY_BASE below to your server URL.
  //   A ready-made Node.js proxy is included as a comment at the bottom of this script.

  const MOMO_CONFIG = {
    // ── CHANGE THESE TO YOUR REAL CREDENTIALS ──
    subscriptionKey: 'YOUR_SUBSCRIPTION_KEY',   // From MTN developer portal
    apiUser:         'YOUR_API_USER_ID',         // UUID you created
    apiKey:          'YOUR_API_KEY',             // From MTN developer portal
    // ── ENVIRONMENT ──
    env:             'sandbox',                  // Change to 'mtnrwanda' for production
    baseUrl:         'https://sandbox.momodeveloper.mtn.com', // Live: https://proxy.momoapi.mtn.com
    // ── YOUR MERCHANT MOMO NUMBER (money goes here) ──
    merchantNumber:  '25078933601',             // Your JVN AI MoMo number (international format)
    // ── PROXY: your backend URL that forwards to MTN (required for browsers) ──
    proxyBase:       '/api/momo',                // e.g. 'https://yourserver.com/api/momo'
  };

  // Format phone to MTN international format: 250XXXXXXXXX
  function formatMoMoPhone(raw) {
    let digits = raw.replace(/\D/g, '');
    if (digits.startsWith('0')) digits = '250' + digits.slice(1);
    if (!digits.startsWith('250')) digits = '250' + digits;
    return digits;
  }

  // Validate MTN Rwanda numbers (078x, 079x)
  function isValidMTNNumber(formatted) {
    return /^25007[89]\d{7}$/.test(formatted);
  }

  // Get MoMo access token via proxy
  async function getMoMoToken() {
    const creds = btoa(MOMO_CONFIG.apiUser + ':' + MOMO_CONFIG.apiKey);
    const res = await fetch(MOMO_CONFIG.proxyBase + '/token', {
      method: 'POST',
      headers: {
        'Authorization': 'Basic ' + creds,
        'Ocp-Apim-Subscription-Key': MOMO_CONFIG.subscriptionKey
      }
    });
    if (!res.ok) throw new Error('Failed to get MoMo token');
    const data = await res.json();
    return data.access_token;
  }

  // Send payment request to payer's phone
  async function sendMoMoRequest(phone, amount, referenceId) {
    const token = await getMoMoToken();
    const res = await fetch(MOMO_CONFIG.proxyBase + '/request-payment', {
      method: 'POST',
      headers: {
        'Authorization': 'Bearer ' + token,
        'X-Reference-Id': referenceId,
        'X-Target-Environment': MOMO_CONFIG.env,
        'Ocp-Apim-Subscription-Key': MOMO_CONFIG.subscriptionKey,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        amount: String(amount),
        currency: 'RWF',
        externalId: referenceId,
        payer: { partyIdType: 'MSISDN', partyId: phone },
        payerMessage: 'JVN AI ' + selectedPlan.name + ' Plan subscription',
        payeeNote: 'JVN AI Education Services'
      })
    });
    if (res.status !== 202) {
      const err = await res.text();
      throw new Error('Payment request failed: ' + err);
    }
    return true;
  }

  // Poll for payment status (PENDING → SUCCESSFUL / FAILED)
  async function pollMoMoStatus(referenceId, maxAttempts = 20) {
    const token = await getMoMoToken();
    for (let i = 0; i < maxAttempts; i++) {
      await new Promise(r => setTimeout(r, 3000)); // wait 3s between polls
      const res = await fetch(MOMO_CONFIG.proxyBase + '/status/' + referenceId, {
        headers: {
          'Authorization': 'Bearer ' + token,
          'X-Target-Environment': MOMO_CONFIG.env,
          'Ocp-Apim-Subscription-Key': MOMO_CONFIG.subscriptionKey
        }
      });
      if (!res.ok) continue;
      const data = await res.json();
      if (data.status === 'SUCCESSFUL') return 'SUCCESSFUL';
      if (data.status === 'FAILED')     return 'FAILED';
      // PENDING → keep polling
    }
    return 'TIMEOUT';
  }

  // Show payment status banner inside the modal
  function showMoMoStatus(type, message) {
    let el = document.getElementById('momo-status-banner');
    if (!el) {
      el = document.createElement('div');
      el.id = 'momo-status-banner';
      el.style.cssText = 'border-radius:10px;padding:10px 14px;font-size:0.8rem;font-weight:600;margin-bottom:1rem;display:flex;align-items:center;gap:8px;';
      document.getElementById('sub-step-2').insertBefore(el, document.getElementById('sub-step-2').querySelector('.momo-input-group'));
    }
    const styles = {
      info:    'background:#e8f4fd;border:1px solid #90c8f0;color:#1565c0;',
      success: 'background:#e8f5ee;border:1px solid #81c995;color:#1b5e20;',
      error:   'background:#fde8e8;border:1px solid #f08080;color:#b71c1c;',
      warning: 'background:#fff8e1;border:1px solid #ffd54f;color:#7a5c00;',
    };
    el.style.cssText += styles[type] || styles.info;
    el.innerHTML = message;
    el.style.display = 'flex';
  }

  function hideMoMoStatus() {
    const el = document.getElementById('momo-status-banner');
    if (el) el.style.display = 'none';
  }

  // ── MAIN PAYMENT HANDLER ──
  async function processMoMoPayment() {
    const rawPhone = document.getElementById('momo-phone').value.trim();
    const name     = document.getElementById('momo-name').value.trim();
    const btn      = document.querySelector('#sub-step-2 button.generate-btn:last-child');

    // Validation
    if (!rawPhone) { showToast('⚠️ Please enter your MTN MoMo phone number'); return; }
    if (!name)     { showToast('⚠️ Please enter your full name'); return; }

    const phone = formatMoMoPhone(rawPhone);
    if (!isValidMTNNumber(phone)) {
      showMoMoStatus('error', '❌ Invalid MTN number. Must be an MTN Rwanda number starting with 078 or 079.');
      return;
    }

    // Lock UI
    btn.textContent = '⏳ Sending request...';
    btn.disabled = true;
    hideMoMoStatus();

    const referenceId = crypto.randomUUID ? crypto.randomUUID() : 'jvn-' + Date.now() + '-' + Math.random().toString(36).slice(2);

    try {
      // 1. Send payment push to user's phone
      showMoMoStatus('info', '📲 Sending payment prompt to <strong>' + rawPhone + '</strong>… Check your phone!');
      await sendMoMoRequest(phone, selectedPlan.price, referenceId);

      // 2. Poll for confirmation
      btn.textContent = '⏳ Waiting for PIN confirmation…';
      showMoMoStatus('warning', '⏳ Waiting for you to enter your MoMo PIN on your phone… (up to 60 seconds)');

      const result = await pollMoMoStatus(referenceId);

      if (result === 'SUCCESSFUL') {
        showMoMoStatus('success', '✅ Payment confirmed! Activating your subscription…');
        await new Promise(r => setTimeout(r, 1000));
        finalizeMoMoSuccess(name, referenceId);
      } else if (result === 'FAILED') {
        showMoMoStatus('error', '❌ Payment was declined or cancelled. Please try again.');
        btn.textContent = '📱 Send MoMo Request';
        btn.disabled = false;
      } else {
        showMoMoStatus('error', '⏱️ No response from your phone. Please try again or dial *182*7*1# to pay manually.');
        btn.textContent = '📱 Send MoMo Request';
        btn.disabled = false;
      }

    } catch (err) {
      console.error('MoMo error:', err);
      // ── SANDBOX DEMO FALLBACK ──
      // If running without a backend proxy, show demo success so UI can be tested
      if (MOMO_CONFIG.subscriptionKey === 'YOUR_SUBSCRIPTION_KEY' || err.message.includes('Failed to fetch')) {
        showMoMoStatus('warning', '🔧 Demo mode — backend proxy not connected. Showing simulated success.');
        btn.textContent = '⏳ Simulating…';
        await new Promise(r => setTimeout(r, 2000));
        finalizeMoMoSuccess(name, referenceId);
      } else {
        showMoMoStatus('error', '❌ Error: ' + err.message + '. Please try again.');
        btn.textContent = '📱 Send MoMo Request';
        btn.disabled = false;
      }
    }
  }

  // ── FINALIZE SUCCESS ──
  function finalizeMoMoSuccess(name, referenceId) {
    const btn = document.querySelector('#sub-step-2 button.generate-btn:last-child');
    btn.textContent = '📱 Send MoMo Request';
    btn.disabled = false;

    const expiry = new Date();
    expiry.setMonth(expiry.getMonth() + 1);
    const expiryStr = expiry.toLocaleDateString('en-RW', { year: 'numeric', month: 'long', day: 'numeric' });

    const teacherName = currentUser ? currentUser.name : name;
    const teacherId   = currentUser ? currentUser.id : 'JVN-' + Math.floor(100000 + Math.random() * 900000);

    document.getElementById('successPlan').textContent     = selectedPlan.name;
    document.getElementById('successName').textContent     = teacherName;
    document.getElementById('successPlanText').textContent = selectedPlan.name + ' Plan — ' + selectedPlan.price.toLocaleString() + ' RWF/month';
    document.getElementById('successId').textContent       = teacherId;
    document.getElementById('successExpiry').textContent   = expiryStr;

    // Persist transaction reference
    if (currentUser) {
      currentUser.lastPaymentRef = referenceId;
      currentUser.plan = selectedPlan.name;
      localStorage.setItem('jvnai_user', JSON.stringify(currentUser));
    }

    goSubStep(3);
  }

  /*
  ════════════════════════════════════════════════════════
  NODE.JS BACKEND PROXY (save as server.js, run with node)
  ════════════════════════════════════════════════════════
  Install: npm install express node-fetch cors uuid

  const express = require('express');
  const fetch   = require('node-fetch');
  const cors    = require('cors');
  const { v4: uuidv4 } = require('uuid');
  const app = express();
  app.use(cors(), express.json());

  const BASE   = 'https://sandbox.momodeveloper.mtn.com'; // or live URL
  const SUBKEY = 'YOUR_SUBSCRIPTION_KEY';
  const USER   = 'YOUR_API_USER';
  const APIKEY = 'YOUR_API_KEY';
  const ENV    = 'sandbox'; // or 'mtnrwanda'

  async function getToken() {
    const creds = Buffer.from(USER + ':' + APIKEY).toString('base64');
    const res = await fetch(BASE + '/collection/token/', {
      method: 'POST',
      headers: { 'Authorization': 'Basic ' + creds, 'Ocp-Apim-Subscription-Key': SUBKEY }
    });
    const data = await res.json();
    return data.access_token;
  }

  app.post('/api/momo/token', async (req, res) => {
    try { res.json({ access_token: await getToken() }); }
    catch(e) { res.status(500).json({ error: e.message }); }
  });

  app.post('/api/momo/request-payment', async (req, res) => {
    try {
      const token = await getToken();
      const refId = req.headers['x-reference-id'] || uuidv4();
      const r = await fetch(BASE + '/collection/v1_0/requesttopay', {
        method: 'POST',
        headers: {
          'Authorization': 'Bearer ' + token,
          'X-Reference-Id': refId,
          'X-Target-Environment': ENV,
          'Ocp-Apim-Subscription-Key': SUBKEY,
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(req.body)
      });
      res.status(r.status).send(await r.text());
    } catch(e) { res.status(500).json({ error: e.message }); }
  });

  app.get('/api/momo/status/:ref', async (req, res) => {
    try {
      const token = await getToken();
      const r = await fetch(BASE + '/collection/v1_0/requesttopay/' + req.params.ref, {
        headers: {
          'Authorization': 'Bearer ' + token,
          'X-Target-Environment': ENV,
          'Ocp-Apim-Subscription-Key': SUBKEY
        }
      });
      res.json(await r.json());
    } catch(e) { res.status(500).json({ error: e.message }); }
  });

  app.listen(3000, () => console.log('MoMo proxy running on port 3000'));
  ════════════════════════════════════════════════════════
  */

  // ── ACTIVATE SUBSCRIPTION ──
  function activateSubscription() {
    if (currentUser) {
      currentUser.plan = selectedPlan.name;
      localStorage.setItem('jvnai_user', JSON.stringify(currentUser));
      updateTeacherBar(currentUser);
    }
    showToast('🎓 ' + selectedPlan.name + ' plan activated! Enjoy JVN AI.');
  }

  // ── AUTO-LOGIN ON PAGE LOAD ──
  window.addEventListener('load', () => {
    const stored = localStorage.getItem('jvnai_user');
    if (stored) {
      try {
        currentUser = JSON.parse(stored);
        updateTeacherBar(currentUser);
      } catch(e) {}
    }
  });
</script>

</body>
</html>
