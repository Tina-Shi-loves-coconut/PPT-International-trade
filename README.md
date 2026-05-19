[index.html](https://github.com/user-attachments/files/28004259/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Switzerland and International Trade Theory</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;600;700&display=swap');

        :root {
            --coral: #E85D5D;
            --coral-dark: #D44A4A;
            --cream: #F5F0E8;
            --cream-dark: #E8E0D4;
            --black: #1A1A1A;
            --gray: #6B6B6B;
            --light-gray: #B0B0B0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            width: 100%;
            height: 100%;
            overflow: hidden;
            font-family: 'Inter', sans-serif;
            background: var(--black);
            color: var(--black);
        }

        .presentation {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .slide {
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.6s ease, visibility 0.6s ease;
            overflow: hidden;
        }

        .slide.active {
            opacity: 1;
            visibility: visible;
        }

        /* Navigation */
        .nav-dots {
            position: fixed;
            right: 24px;
            top: 50%;
            transform: translateY(-50%);
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .nav-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255,255,255,0.3);
            border: 2px solid rgba(255,255,255,0.5);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .nav-dot.active {
            background: var(--coral);
            border-color: var(--coral);
        }

        .nav-dot.dark {
            background: rgba(26,26,26,0.2);
            border-color: rgba(26,26,26,0.4);
        }

        .nav-dot.dark.active {
            background: var(--coral);
            border-color: var(--coral);
        }

        .slide-counter {
            position: fixed;
            bottom: 24px;
            right: 24px;
            z-index: 1000;
            font-family: 'Bebas Neue', sans-serif;
            font-size: 18px;
            letter-spacing: 2px;
            color: rgba(255,255,255,0.6);
        }

        .slide-counter.dark {
            color: rgba(26,26,26,0.5);
        }

        /* Arrow Navigation */
        .nav-arrows {
            position: fixed;
            bottom: 24px;
            left: 24px;
            z-index: 1000;
            display: flex;
            gap: 16px;
        }

        .nav-arrow {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            border: 2px solid rgba(255,255,255,0.3);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 18px;
        }

        .nav-arrow:hover {
            background: var(--coral);
            border-color: var(--coral);
        }

        .nav-arrow.dark {
            background: rgba(26,26,26,0.05);
            border-color: rgba(26,26,26,0.2);
            color: var(--black);
        }

        .nav-arrow.dark:hover {
            background: var(--coral);
            border-color: var(--coral);
            color: white;
        }

        /* ===== SLIDE 1: TITLE / COVER ===== */
        .slide-1 {
            display: grid;
            grid-template-rows: 32% 68%;
        }

        .slide-1 .top-section {
            background: var(--coral);
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: flex-start;
            justify-content: flex-start;
            padding: clamp(24px, 4vh, 48px) clamp(40px, 8vw, 100px);
        }

        .slide-1 .zigzag-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .slide-1 .zigzag-layer svg {
            width: 100%;
            height: 100%;
        }

        .slide-1 .brand-mark {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 4px;
            color: var(--black);
            position: relative;
            z-index: 2;
            opacity: 0.7;
        }

        .slide-1 .bottom-section {
            background: var(--cream);
            padding: clamp(28px, 4.5vh, 60px) clamp(40px, 8vw, 100px) clamp(24px, 3.5vh, 44px);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            min-height: 0;
        }

        .slide-1 .main-title {
            font-family: 'Bebas Neue', sans-serif;
            /* Cap by both viewport WIDTH and HEIGHT so the 3-line title
               can never grow taller than the bottom-section can hold.
               Without the vh cap the title overflows on short laptops. */
            font-size: min(120px, 9vw, 13vh);
            color: var(--black);
            line-height: 0.9;
            letter-spacing: 4px;
        }

        .slide-1 .title-rule {
            width: 100%;
            height: 3px;
            background: var(--black);
            margin-top: clamp(16px, 2.5vh, 32px);
            opacity: 0.15;
        }

        .slide-1 .meta-row {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-top: auto;
            padding-top: clamp(16px, 2.5vh, 32px);
        }

        .slide-1 .meta-left {
            display: flex;
            flex-direction: column;
            gap: 2px;
        }

        .slide-1 .meta-right {
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 2px;
        }

        .slide-1 .meta-label {
            font-family: 'Inter', sans-serif;
            font-size: 11px;
            font-weight: 600;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--gray);
        }

        .slide-1 .meta-value {
            font-family: 'Bebas Neue', sans-serif;
            font-size: min(44px, 3.5vw, 5.5vh);
            color: var(--black);
            letter-spacing: 2px;
            line-height: 1;
        }

        .slide-1 .meta-date {
            font-family: 'Bebas Neue', sans-serif;
            font-size: min(38px, 3vw, 4.8vh);
            color: var(--black);
            letter-spacing: 2px;
            line-height: 1;
        }

        /* ===== SLIDE 2: INTRODUCTION ===== */
        .slide-2 {
            background: var(--cream);
            display: flex;
            flex-direction: column;
            padding: clamp(40px, 6vh, 80px) clamp(40px, 8vw, 100px);
        }

        .slide-2 .section-label {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--coral);
            margin-bottom: 24px;
        }

        .slide-2 .big-statement {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(42px, 7vw, 100px);
            color: var(--black);
            line-height: 1.0;
            letter-spacing: 2px;
            max-width: 90%;
            margin-bottom: 32px;
        }

        .slide-2 .body-text {
            font-family: 'Inter', sans-serif;
            font-size: clamp(15px, 1.4vw, 20px);
            line-height: 1.7;
            color: var(--gray);
            max-width: 600px;
        }

        .slide-2 .accent-line {
            width: 80px;
            height: 4px;
            background: var(--coral);
            margin-top: auto;
        }

        /* ===== SLIDE 3: TWO COLUMN ===== */
        .slide-3 {
            background: var(--black);
            display: grid;
            grid-template-columns: 1fr 1fr;
        }

        .slide-3 .left-col {
            background: var(--coral);
            padding: clamp(40px, 6vh, 80px) clamp(32px, 4vw, 60px);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            overflow: hidden;
        }

        .slide-3 .left-col::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -30%;
            width: 80%;
            height: 200%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 20px,
                rgba(0,0,0,0.06) 20px,
                rgba(0,0,0,0.06) 40px
            );
        }

        .slide-3 .left-col .number {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(100px, 15vw, 200px);
            color: rgba(0,0,0,0.12);
            line-height: 1;
            position: relative;
        }

        .slide-3 .left-col .col-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(36px, 5vw, 72px);
            color: var(--black);
            line-height: 1;
            letter-spacing: 2px;
            position: relative;
            z-index: 2;
        }

        .slide-3 .right-col {
            padding: clamp(40px, 6vh, 80px) clamp(32px, 4vw, 60px);
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .slide-3 .right-col .item {
            margin-bottom: 28px;
        }

        .slide-3 .right-col .item:last-child {
            margin-bottom: 0;
        }

        .slide-3 .right-col .item-label {
            font-family: 'Inter', sans-serif;
            font-size: 11px;
            font-weight: 700;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--coral);
            margin-bottom: 8px;
        }

        .slide-3 .right-col .item-text {
            font-family: 'Inter', sans-serif;
            font-size: clamp(14px, 1.2vw, 18px);
            color: var(--cream);
            line-height: 1.6;
        }

        /* ===== SLIDE 4: CHART / DATA ===== */
        .slide-4 {
            background: var(--cream);
            display: flex;
            flex-direction: column;
            padding: clamp(40px, 6vh, 80px) clamp(40px, 8vw, 100px);
        }

        .slide-4 .slide-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 40px;
        }

        .slide-4 .header-left .section-label {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--coral);
            margin-bottom: 12px;
        }

        .slide-4 .header-left .slide-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(40px, 6vw, 80px);
            color: var(--black);
            line-height: 1;
            letter-spacing: 2px;
        }

        .slide-4 .header-right {
            text-align: right;
        }

        .slide-4 .stat-number {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(48px, 7vw, 96px);
            color: var(--coral);
            line-height: 1;
        }

        .slide-4 .stat-label {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            color: var(--gray);
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .slide-4 .chart-container {
            flex: 1;
            display: flex;
            gap: 40px;
            align-items: stretch;
            min-height: 0;
        }

        .slide-4 .chart-wrapper {
            flex: 2;
            position: relative;
            min-height: 0;
        }

        .slide-4 .chart-wrapper canvas {
            max-height: 100%;
        }

        .slide-4 .chart-sidebar {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 20px;
            justify-content: center;
        }

        .slide-4 .sidebar-item {
            background: white;
            padding: 20px 24px;
            border-left: 4px solid var(--coral);
        }

        .slide-4 .sidebar-item .value {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(28px, 3vw, 48px);
            color: var(--black);
            line-height: 1;
        }

        .slide-4 .sidebar-item .label {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            color: var(--gray);
            margin-top: 4px;
            letter-spacing: 1px;
        }

        /* ===== SLIDE 5: FULL WIDTH FEATURE ===== */
        .slide-5 {
            display: grid;
            grid-template-rows: 1fr auto;
            background: var(--black);
        }

        .slide-5 .visual-area {
            background: linear-gradient(135deg, var(--coral-dark) 0%, var(--coral) 100%);
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .slide-5 .visual-area .pattern-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.1;
            background-image: repeating-linear-gradient(
                90deg,
                transparent,
                transparent 60px,
                var(--black) 60px,
                var(--black) 62px
            );
        }

        .slide-5 .visual-area .center-text {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(80px, 15vw, 200px);
            color: var(--black);
            letter-spacing: 12px;
            position: relative;
            z-index: 2;
            text-align: center;
        }

        .slide-5 .info-bar {
            background: var(--cream);
            padding: clamp(24px, 4vh, 40px) clamp(40px, 8vw, 100px);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .slide-5 .info-bar .bar-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(28px, 4vw, 56px);
            color: var(--black);
            letter-spacing: 2px;
        }

        .slide-5 .info-bar .bar-meta {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            color: var(--gray);
            letter-spacing: 2px;
            text-transform: uppercase;
            text-align: right;
        }

        /* ===== SLIDE 6: THREE COLUMNS ===== */
        .slide-6 {
            background: var(--cream);
            display: flex;
            flex-direction: column;
            padding: clamp(40px, 6vh, 80px) clamp(40px, 8vw, 100px);
        }

        .slide-6 .slide-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(40px, 6vw, 80px);
            color: var(--black);
            line-height: 1;
            letter-spacing: 2px;
            margin-bottom: 8px;
        }

        .slide-6 .slide-subtitle {
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            color: var(--gray);
            letter-spacing: 2px;
            margin-bottom: 48px;
        }

        .slide-6 .columns-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 32px;
            flex: 1;
        }

        .slide-6 .column-card {
            background: white;
            padding: clamp(24px, 3vh, 40px);
            border-top: 5px solid var(--coral);
            display: flex;
            flex-direction: column;
        }

        .slide-6 .column-card .card-icon {
            width: 48px;
            height: 48px;
            background: var(--coral);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Bebas Neue', sans-serif;
            font-size: 24px;
            color: white;
        }

        .slide-6 .column-card .card-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(24px, 2.5vw, 36px);
            color: var(--black);
            letter-spacing: 1px;
            margin-bottom: 12px;
            line-height: 1.1;
        }

        .slide-6 .column-card .card-text {
            font-family: 'Inter', sans-serif;
            font-size: clamp(13px, 1.1vw, 16px);
            color: var(--gray);
            line-height: 1.6;
            flex: 1;
        }

        .slide-6 .column-card .card-stat {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(36px, 4vw, 56px);
            color: var(--coral);
            line-height: 1;
            margin-top: auto;
            padding-top: 20px;
        }

        /* ===== SLIDE 7: QUOTE ===== */
        .slide-7 {
            background: var(--black);
            display: grid;
            grid-template-columns: 40% 60%;
        }

        .slide-7 .quote-left {
            background: var(--coral);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .slide-7 .quote-left::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                -45deg,
                transparent,
                transparent 30px,
                rgba(0,0,0,0.06) 30px,
                rgba(0,0,0,0.06) 60px
            );
        }

        .slide-7 .quote-left .giant-mark {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(140px, 20vw, 280px);
            color: var(--black);
            opacity: 0.35;
            line-height: 1;
            position: relative;
            z-index: 2;
        }

        .slide-7 .quote-right {
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: clamp(40px, 8vh, 100px) clamp(48px, 7vw, 100px);
        }

        .slide-7 .quote-text {
            font-family: 'Inter', sans-serif;
            font-size: clamp(20px, 2.5vw, 36px);
            font-weight: 300;
            color: var(--cream);
            line-height: 1.5;
            
            margin-bottom: 40px;
        }

        .slide-7 .quote-author {
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            font-weight: 600;
            color: var(--coral);
            letter-spacing: 3px;
            text-transform: uppercase;
        }

        .slide-7 .quote-role {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            color: var(--gray);
            margin-top: 4px;
            letter-spacing: 1px;
        }

        .slide-7 .quote-accent {
            width: 60px;
            height: 4px;
            background: var(--coral);
            margin-bottom: 32px;
        }

        /* ===== SLIDE 8: TIMELINE / DIAGRAM ===== */
        .slide-8 {
            background: var(--cream);
            display: flex;
            flex-direction: column;
            padding: clamp(40px, 6vh, 80px) clamp(40px, 8vw, 100px);
        }

        .slide-8 .slide-header {
            margin-bottom: 48px;
        }

        .slide-8 .section-label {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--coral);
            margin-bottom: 12px;
        }

        .slide-8 .slide-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(40px, 6vw, 80px);
            color: var(--black);
            line-height: 1;
            letter-spacing: 2px;
        }

        .slide-8 .timeline-container {
            flex: 1;
            display: flex;
            align-items: center;
            position: relative;
        }

        .slide-8 .timeline-line {
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--black);
            transform: translateY(-50%);
        }

        .slide-8 .timeline-line::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                90deg,
                var(--black) 0px,
                var(--black) 20px,
                transparent 20px,
                transparent 30px
            );
        }

        .slide-8 .timeline-points {
            display: flex;
            justify-content: space-between;
            width: 100%;
            position: relative;
            z-index: 2;
        }

        .slide-8 .t-point {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 18%;
        }

        .slide-8 .t-point:nth-child(odd) .t-bubble {
            margin-bottom: 24px;
            order: 1;
        }

        .slide-8 .t-point:nth-child(odd) .t-info {
            order: 2;
            text-align: center;
        }

        .slide-8 .t-point:nth-child(even) .t-bubble {
            margin-top: 24px;
            order: 2;
        }

        .slide-8 .t-point:nth-child(even) .t-info {
            order: 1;
            text-align: center;
            margin-bottom: 20px;
        }

        .slide-8 .t-bubble {
            width: clamp(60px, 8vw, 100px);
            height: clamp(60px, 8vw, 100px);
            border-radius: 50%;
            background: var(--coral);
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(20px, 2vw, 32px);
            color: white;
            border: 4px solid var(--black);
            flex-shrink: 0;
        }

        .slide-8 .t-info .t-phase {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--coral);
            margin-bottom: 4px;
        }

        .slide-8 .t-info .t-desc {
            font-family: 'Inter', sans-serif;
            font-size: clamp(12px, 1vw, 14px);
            color: var(--gray);
            line-height: 1.4;
        }

        /* ===== SLIDE 9: TEAM GRID ===== */
        .slide-9 {
            background: var(--black);
            display: flex;
            flex-direction: column;
            padding: clamp(40px, 6vh, 80px) clamp(40px, 8vw, 100px);
        }

        .slide-9 .slide-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(40px, 6vw, 80px);
            color: var(--cream);
            line-height: 1;
            letter-spacing: 2px;
            margin-bottom: 8px;
        }

        .slide-9 .slide-subtitle {
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            color: var(--gray);
            letter-spacing: 2px;
            margin-bottom: 48px;
        }

        .slide-9 .team-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 24px;
            flex: 1;
        }

        .slide-9 .team-member {
            background: rgba(245, 240, 232, 0.05);
            padding: clamp(20px, 2vh, 32px);
            border: 1px solid rgba(245, 240, 232, 0.1);
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            transition: all 0.3s ease;
        }

        .slide-9 .team-member:hover {
            background: rgba(232, 93, 93, 0.1);
            border-color: var(--coral);
        }

        .slide-9 .member-avatar {
            width: clamp(60px, 8vw, 100px);
            height: clamp(60px, 8vw, 100px);
            border-radius: 50%;
            background: linear-gradient(135deg, var(--coral) 0%, var(--coral-dark) 100%);
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(28px, 3vw, 40px);
            color: white;
        }

        .slide-9 .member-name {
            font-family: 'Inter', sans-serif;
            font-size: 16px;
            font-weight: 600;
            color: var(--cream);
            margin-bottom: 4px;
        }

        .slide-9 .member-role {
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            color: var(--gray);
            letter-spacing: 1px;
        }

        /* ===== SLIDE 10: CLOSING ===== */
        .slide-10 {
            display: grid;
            grid-template-columns: 55% 45%;
        }

        .slide-10 .left-panel {
            background: var(--coral);
            padding: clamp(40px, 8vh, 100px) clamp(40px, 6vw, 80px);
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .slide-10 .left-panel .closing-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(48px, 8vw, 120px);
            color: var(--black);
            line-height: 0.95;
            letter-spacing: 4px;
            margin-bottom: 24px;
        }

        .slide-10 .left-panel .closing-subtitle {
            font-family: 'Inter', sans-serif;
            font-size: clamp(14px, 1.3vw, 20px);
            color: rgba(0,0,0,0.7);
            line-height: 1.6;
            max-width: 400px;
        }

        .slide-10 .left-panel .zigzag-deco {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 60px;
            opacity: 0.2;
        }

        .slide-10 .right-panel {
            background: var(--cream);
            padding: clamp(40px, 8vh, 100px) clamp(40px, 6vw, 80px);
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .slide-10 .contact-block {
            margin-bottom: 32px;
        }

        .slide-10 .contact-block:last-child {
            margin-bottom: 0;
        }

        .slide-10 .contact-label {
            font-family: 'Inter', sans-serif;
            font-size: 11px;
            font-weight: 700;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: var(--gray);
            margin-bottom: 8px;
        }

        .slide-10 .contact-value {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(24px, 3vw, 40px);
            color: var(--black);
            letter-spacing: 2px;
            line-height: 1.1;
        }

        .slide-10 .social-row {
            display: flex;
            gap: 16px;
            margin-top: 40px;
        }

        .slide-10 .social-icon {
            width: 44px;
            height: 44px;
            border: 2px solid var(--black);
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Inter', sans-serif;
            font-size: 12px;
            font-weight: 700;
            color: var(--black);
            transition: all 0.3s ease;
        }

        .slide-10 .social-icon:hover {
            background: var(--coral);
            border-color: var(--coral);
            color: white;
        }

        /* Coral chart inserts */
        .deck-figure {
            display: block;
            background: var(--cream);
            border: 3px solid var(--black);
            box-shadow: 12px 12px 0 var(--coral);
            object-fit: contain;
        }

        .slide-2.with-figure .big-statement {
            max-width: 53%;
            font-size: clamp(36px, 5vw, 68px);
        }

        .slide-2.with-figure .body-text {
            max-width: 47%;
        }

        .slide-2 .intro-figure {
            position: absolute;
            right: clamp(52px, 7vw, 92px);
            bottom: clamp(74px, 10vh, 118px);
            width: min(45vw, 680px);
            max-height: 45vh;
        }

        .slide-4 .chart-wrapper .deck-figure {
            width: 100%;
            height: 100%;
            box-shadow: 10px 10px 0 var(--coral);
        }

        .slide-5.with-figure .visual-area {
            align-items: center;
            justify-content: flex-start;
            padding-left: clamp(44px, 7vw, 96px);
        }

        .slide-5.with-figure .visual-area .center-text {
            font-size: clamp(70px, 10vw, 150px);
            letter-spacing: 8px;
            max-width: 38%;
            color: var(--black);
        }

        .slide-5 .factor-figure {
            position: absolute;
            right: clamp(42px, 6vw, 90px);
            top: 10%;
            width: min(55vw, 760px);
            max-height: 76%;
            z-index: 3;
        }

        .slide-6.with-figure .slide-title {
            max-width: 52%;
        }

        .slide-6.with-figure .slide-subtitle {
            max-width: 43%;
        }

        .slide-6.with-figure .columns-grid {
            grid-template-columns: 1fr;
            width: 40%;
            gap: 12px;
            margin-top: 20px;
        }

        .slide-6.with-figure .column-card {
            min-height: 0;
            padding: 16px 18px;
        }

        .slide-6.with-figure .column-card .card-icon {
            width: 36px;
            height: 36px;
            font-size: 16px;
            margin-bottom: 8px;
        }

        .slide-6.with-figure .column-card .card-title {
            font-size: clamp(21px, 2vw, 30px);
            margin-bottom: 6px;
        }

        .slide-6.with-figure .column-card .card-text {
            font-size: clamp(11px, 1vw, 14px);
            line-height: 1.35;
            margin-bottom: 8px;
        }

        .slide-6.with-figure .column-card .card-stat {
            font-size: clamp(26px, 3vw, 42px);
            padding-top: 4px;
        }

        .slide-6 .scale-figure,
        .slide-6 .dependence-figure {
            position: absolute;
            right: clamp(54px, 7vw, 96px);
            bottom: clamp(70px, 9vh, 110px);
            width: min(48vw, 740px);
            max-height: 57vh;
        }

        .slide-6.scale-slide .slide-title {
            font-size: clamp(34px, 5vw, 64px);
            margin-bottom: 8px;
        }

        .slide-6.scale-slide .slide-subtitle {
            font-size: 13px;
            line-height: 1.45;
            margin-bottom: 8px;
            max-width: 38%;
        }

        .slide-6.scale-slide .columns-grid {
            width: 37%;
            gap: 8px;
            margin-top: 8px;
        }

        .slide-6.scale-slide .column-card {
            display: grid;
            grid-template-columns: 42px 1fr;
            grid-template-areas:
                "icon title"
                "stat text";
            column-gap: 12px;
            row-gap: 4px;
            padding: 10px 12px;
            align-items: start;
        }

        .slide-6.scale-slide .column-card .card-icon {
            grid-area: icon;
            width: 38px;
            height: 38px;
            margin: 0;
        }

        .slide-6.scale-slide .column-card .card-title {
            grid-area: title;
            font-size: clamp(20px, 1.8vw, 28px);
            margin: 0;
            line-height: 1;
        }

        .slide-6.scale-slide .column-card .card-text {
            grid-area: text;
            font-size: clamp(10px, 0.9vw, 13px);
            line-height: 1.28;
            margin: 0;
        }

        .slide-6.scale-slide .column-card .card-stat {
            grid-area: stat;
            font-size: clamp(20px, 2.3vw, 34px);
            margin: 0;
            padding: 0;
            align-self: end;
        }

        .slide-6.scale-slide .scale-figure {
            width: min(47vw, 700px);
            max-height: 50vh;
            right: clamp(46px, 6vw, 82px);
            bottom: clamp(66px, 8vh, 96px);
        }

        .slide-6.political-slide .slide-title {
            font-size: clamp(34px, 5vw, 64px);
            margin-bottom: 8px;
        }

        .slide-6.political-slide .slide-subtitle {
            font-size: 13px;
            line-height: 1.45;
            margin-bottom: 8px;
            max-width: 38%;
        }

        .slide-6.political-slide .columns-grid {
            width: 37%;
            gap: 8px;
            margin-top: 8px;
        }

        .slide-6.political-slide .column-card {
            display: grid;
            grid-template-columns: 42px 1fr;
            grid-template-areas:
                "icon title"
                "stat text";
            column-gap: 12px;
            row-gap: 4px;
            padding: 10px 12px;
            align-items: start;
        }

        .slide-6.political-slide .column-card .card-icon {
            grid-area: icon;
            width: 38px;
            height: 38px;
            margin: 0;
        }

        .slide-6.political-slide .column-card .card-title {
            grid-area: title;
            font-size: clamp(20px, 1.8vw, 28px);
            margin: 0;
            line-height: 1;
        }

        .slide-6.political-slide .column-card .card-text {
            grid-area: text;
            font-size: clamp(10px, 0.9vw, 13px);
            line-height: 1.28;
            margin: 0;
        }

        .slide-6.political-slide .column-card .card-stat {
            grid-area: stat;
            font-size: clamp(20px, 2.3vw, 34px);
            margin: 0;
            padding: 0;
            align-self: end;
        }

        .slide-6.political-slide .dependence-figure {
            width: min(47vw, 700px);
            max-height: 50vh;
            right: clamp(46px, 6vw, 82px);
            bottom: clamp(66px, 8vh, 96px);
        }

        .slide-7.with-figure .quote-right {
            justify-content: center;
        }

        .slide-7.with-figure .quote-accent {
            margin-bottom: 18px;
        }

        .slide-7.with-figure .quote-text {
            font-size: clamp(24px, 3vw, 42px);
            margin-bottom: 16px;
        }

        .slide-7.with-figure .quote-author {
            margin-top: 0;
        }

        .slide-7 .firms-figure {
            width: min(46vw, 680px);
            max-height: 33vh;
            margin-top: 24px;
            box-shadow: 10px 10px 0 var(--coral);
        }

        .slide-8.with-figure .slide-header {
            margin-bottom: 18px;
        }

        .slide-8 .distribution-figure {
            align-self: flex-end;
            width: min(57vw, 780px);
            max-height: 30vh;
            margin-top: -8px;
            margin-bottom: 16px;
            box-shadow: 10px 10px 0 var(--coral);
        }

        .slide-8.with-figure .timeline-container {
            flex: 0 0 42%;
            min-height: 280px;
        }

        .slide-9.with-figure .slide-title {
            font-size: clamp(36px, 5vw, 66px);
        }

        .slide-9.with-figure .slide-subtitle {
            margin-bottom: 18px;
        }

        .slide-9.with-figure .team-grid {
            grid-template-columns: repeat(4, 1fr);
            gap: 14px;
            flex: 0 0 auto;
        }

        .slide-9.with-figure .team-member {
            min-height: 0;
            padding: 16px 12px;
        }

        .slide-9.with-figure .member-avatar {
            width: 58px;
            height: 58px;
            font-size: 18px;
            margin-bottom: 12px;
        }

        .slide-9.with-figure .member-name {
            font-size: clamp(22px, 2vw, 30px);
        }

        .slide-9.with-figure .member-role {
            font-size: clamp(11px, 1vw, 14px);
        }

        .slide-9 .tariff-figure {
            width: min(60vw, 840px);
            max-height: 34vh;
            margin: 22px auto 0;
            box-shadow: 10px 10px 0 var(--coral);
        }

        .slide-3.with-figure {
            grid-template-columns: 36% 64%;
        }

        .slide-3.with-figure .right-col {
            gap: 16px;
            justify-content: center;
            padding-top: 6vh;
            padding-bottom: 6vh;
        }

        .slide-3.with-figure .right-col .item {
            padding-bottom: 16px;
        }

        .slide-3.with-figure .tariff-impact-figure {
            width: min(50vw, 760px);
            max-height: 31vh;
            margin-top: 10px;
            box-shadow: 10px 10px 0 var(--coral);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .slide-3 {
                grid-template-columns: 1fr;
                grid-template-rows: 40% 60%;
            }

            .slide-6 .columns-grid {
                grid-template-columns: 1fr;
                gap: 16px;
            }

            .slide-8 .timeline-container {
                overflow-x: auto;
            }

            .slide-8 .timeline-points {
                min-width: 600px;
            }

            .slide-9 .team-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .slide-10 {
                grid-template-columns: 1fr;
                grid-template-rows: 50% 50%;
            }

            .slide-4 .chart-container {
                flex-direction: column;
            }

            .slide-7 {
                grid-template-columns: 1fr;
                grid-template-rows: 35% 65%;
            }

            .slide-7 .quote-left {
                min-height: 200px;
            }

            .slide-2.with-figure .big-statement,
            .slide-2.with-figure .body-text {
                max-width: 100%;
            }

            .slide-2 .intro-figure {
                position: relative;
                right: auto;
                bottom: auto;
                width: 72vw;
                max-height: 28vh;
                margin-top: 18px;
                align-self: flex-end;
            }

            .slide-5.with-figure .visual-area {
                padding: 24px 40px;
                flex-direction: column;
                justify-content: center;
                gap: 18px;
            }

            .slide-5.with-figure .visual-area .center-text {
                max-width: 100%;
                font-size: clamp(48px, 16vw, 96px);
            }

            .slide-5 .factor-figure {
                position: relative;
                right: auto;
                top: auto;
                width: 76vw;
                max-height: 38vh;
            }

            .slide-6.with-figure .slide-title,
            .slide-6.with-figure .slide-subtitle {
                max-width: 100%;
            }

            .slide-6.with-figure .columns-grid {
                width: 100%;
                grid-template-columns: 1fr;
            }

            .slide-6 .scale-figure,
            .slide-6 .dependence-figure,
            .slide-3.with-figure .tariff-impact-figure {
                position: relative;
                right: auto;
                bottom: auto;
                width: 76vw;
                max-height: 24vh;
                margin: 12px auto 0;
            }

            .slide-7 .firms-figure,
            .slide-8 .distribution-figure,
            .slide-9 .tariff-figure {
                width: 76vw;
                max-height: 24vh;
            }

            .slide-8.with-figure .timeline-container {
                min-height: 240px;
            }

            .slide-9.with-figure .team-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="presentation">
        <!-- Slide 1: Title / Cover -->
        <div class="slide slide-1 active">
            <div class="top-section">
                <div class="zigzag-layer">
                    <svg viewBox="0 0 1200 400" preserveAspectRatio="xMidYMid slice">
                        <polyline points="-50,320 50,120 150,320 250,120 350,320 450,120 550,320 650,120 750,320 850,120 950,320 1050,120 1150,320 1250,120" 
                                  fill="none" stroke="#1A1A1A" stroke-width="18" stroke-linejoin="miter" stroke-linecap="butt" opacity="0.22"/>
                        <polyline points="-50,380 50,180 150,380 250,180 350,380 450,180 550,380 650,180 750,380 850,180 950,380 1050,180 1150,380 1250,180" 
                                  fill="none" stroke="#1A1A1A" stroke-width="12" stroke-linejoin="miter" stroke-linecap="butt" opacity="0.15"/>
                    </svg>
                </div>
                <div class="brand-mark">INTERNATIONAL TRADE</div>
            </div>
            <div class="bottom-section">
                <div>
                    <div class="main-title">SWITZERLAND<br>AND INTERNATIONAL<br>TRADE THEORY</div>
                    <div class="title-rule"></div>
                </div>
                <div class="meta-row">
                    <div class="meta-left">
                        <div class="meta-label">Student</div>
                        <div class="meta-value">QINHAN SHI</div>
                    </div>
                    <div class="meta-right">
                        <div class="meta-label">Comparative Advantage, Innovation, and U.S. Tariff Impacts</div>
                        <div class="meta-date">2026.5.21</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 2: Introduction -->
        <div class="slide slide-2 with-figure">
            <div class="section-label">01 / Introduction</div>
            <div class="big-statement">SWITZERLAND WINS TRADE THROUGH PRODUCTIVITY, NOT RESOURCES</div>
            <div class="body-text">
                Switzerland is a small open economy with strong export dependence. Its global position is built on
                pharmaceuticals, chemicals, precision machinery, watches, and financial services, with the European
                Union, the United States, and China as major trading partners.
            </div>
            <img class="deck-figure intro-figure" src="assets/coral-charts/figure1_swiss_exports_composition_coral.png" alt="Composition of Swiss exports in 2025">
            <div class="accent-line"></div>
        </div>

        <!-- Slide 3: Thesis and Theoretical Framework -->
        <div class="slide slide-3">
            <div class="left-col">
                <div class="number">02</div>
                <div class="col-title">THESIS<br>FRAMEWORK</div>
            </div>
            <div class="right-col">
                <div class="item">
                    <div class="item-label">Thesis Statement</div>
                    <div class="item-text">Switzerland's trade success is based on human capital, technological innovation, and economies of scale.</div>
                </div>
                <div class="item">
                    <div class="item-label">Core Theories</div>
                    <div class="item-text">Comparative advantage, Heckscher-Ohlin, economies of scale, firm heterogeneity, and trade policy.</div>
                </div>
                <div class="item">
                    <div class="item-label">Policy Shock</div>
                    <div class="item-text">Recent U.S. tariffs exposed the vulnerability of small open economies to protectionism.</div>
                </div>
            </div>
        </div>

        <!-- Slide 4: Comparative Advantage -->
        <div class="slide slide-4">
            <div class="slide-header">
                <div class="header-left">
                    <div class="section-label">03 / Ricardian Model</div>
                    <div class="slide-title">COMPARATIVE ADVANTAGE</div>
                </div>
                <div class="header-right">
                    <div class="stat-number">R&amp;D</div>
                    <div class="stat-label">Productivity Edge</div>
                </div>
            </div>
            <div class="chart-container">
                <div class="chart-wrapper">
                    <img class="deck-figure" src="assets/coral-charts/figure2_exports_to_us_coral.png" alt="Major Swiss exports to the United States in 2024">
                </div>
                <div class="chart-sidebar">
                    <div class="sidebar-item">
                        <div class="value">SKILL</div>
                        <div class="label">Highly trained labor force</div>
                    </div>
                    <div class="sidebar-item">
                        <div class="value">TECH</div>
                        <div class="label">Research and innovation capacity</div>
                    </div>
                    <div class="sidebar-item">
                        <div class="value">FIRMS</div>
                        <div class="label">Novartis and Roche</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 5: Heckscher-Ohlin Model -->
        <div class="slide slide-5 with-figure">
            <div class="visual-area">
                <div class="pattern-overlay"></div>
                <div class="center-text">FACTOR</div>
                <img class="deck-figure factor-figure" src="assets/coral-charts/figure3_factor_endowments_coral.png" alt="Swiss factor endowments">
            </div>
            <div class="info-bar">
                <div class="bar-title">HUMAN CAPITAL OVER NATURAL RESOURCES</div>
                <div class="bar-meta">Exports: skilled-labor and capital-intensive goods<br>Imports: raw materials and lower-cost manufactured goods</div>
            </div>
        </div>

        <!-- Slide 6: Economies of Scale -->
        <div class="slide slide-6 with-figure scale-slide">
            <div class="slide-title">ECONOMIES OF SCALE</div>
            <div class="slide-subtitle">Large global markets help Swiss firms spread high fixed R&amp;D costs</div>
            <div class="columns-grid">
                <div class="column-card">
                    <div class="card-icon">P</div>
                    <div class="card-title">PHARMA</div>
                    <div class="card-text">Research-heavy production benefits from serving global demand rather than only the domestic market.</div>
                    <div class="card-stat">R&amp;D</div>
                </div>
                <div class="column-card">
                    <div class="card-icon">M</div>
                    <div class="card-title">MEDTECH</div>
                    <div class="card-text">Specialized equipment and standards create cost advantages as output and experience expand.</div>
                    <div class="card-stat">SCALE</div>
                </div>
                <div class="column-card">
                    <div class="card-icon">N</div>
                    <div class="card-title">NEW TRADE</div>
                    <div class="card-text">Krugman's New Trade Theory explains why scale and product differentiation reinforce export performance.</div>
                    <div class="card-stat">NTT</div>
                </div>
            </div>
            <img class="deck-figure scale-figure" src="assets/coral-charts/figure4_economies_of_scale_coral.png" alt="Economies of scale in Swiss pharmaceutical production">
        </div>

        <!-- Slide 7: Firm Heterogeneity -->
        <div class="slide slide-7 with-figure">
            <div class="quote-left">
                <div class="giant-mark">M</div>
            </div>
            <div class="quote-right">
                <div class="quote-accent"></div>
                <div class="quote-text">The Melitz model explains why only the most productive firms can absorb export costs and compete internationally.</div>
                <div class="quote-author">Nestle, ABB, Roche, Novartis</div>
                <div class="quote-role">Large innovative exporters</div>
                <img class="deck-figure firms-figure" src="assets/coral-charts/figure5_global_firms_coral.png" alt="Global presence of major Swiss firms">
            </div>
        </div>

        <!-- Slide 8: Distributional Effects -->
        <div class="slide slide-8 with-figure">
            <div class="slide-header">
                <div class="section-label">07 / Stolper-Samuelson</div>
                <div class="slide-title">WINNERS AND LOSERS</div>
            </div>
            <img class="deck-figure distribution-figure" src="assets/coral-charts/figure6_distributional_effects_coral.png" alt="Distributional effects of trade in Switzerland">
            <div class="timeline-container">
                <div class="timeline-line"></div>
                <div class="timeline-points">
                    <div class="t-point">
                        <div class="t-bubble">01</div>
                        <div class="t-info">
                            <div class="t-phase">Skilled workers</div>
                            <div class="t-desc">Gain from demand in export-oriented high-productivity sectors</div>
                        </div>
                    </div>
                    <div class="t-point">
                        <div class="t-bubble">02</div>
                        <div class="t-info">
                            <div class="t-phase">Financial sector</div>
                            <div class="t-desc">Benefits from Switzerland's global service and capital networks</div>
                        </div>
                    </div>
                    <div class="t-point">
                        <div class="t-bubble">03</div>
                        <div class="t-info">
                            <div class="t-phase">Export industries</div>
                            <div class="t-desc">Capture global demand in pharma, watches, chemicals, and precision goods</div>
                        </div>
                    </div>
                    <div class="t-point">
                        <div class="t-bubble">04</div>
                        <div class="t-info">
                            <div class="t-phase">Low-skilled workers</div>
                            <div class="t-desc">Face weaker bargaining power in sectors exposed to import competition</div>
                        </div>
                    </div>
                    <div class="t-point">
                        <div class="t-bubble">05</div>
                        <div class="t-info">
                            <div class="t-phase">Traditional manufacturing</div>
                            <div class="t-desc">May lose from lower-cost foreign competition and structural adjustment</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 9: Swiss Trade Policy -->
        <div class="slide slide-9 with-figure">
            <div class="slide-title">TRADE POLICY</div>
            <div class="slide-subtitle">Open economy, selective protection</div>
            <div class="team-grid">
                <div class="team-member">
                    <div class="member-avatar">WTO</div>
                    <div class="member-name">Rules-Based Trade</div>
                    <div class="member-role">Supports multilateral institutions</div>
                </div>
                <div class="team-member">
                    <div class="member-avatar">FTA</div>
                    <div class="member-name">Bilateral Agreements</div>
                    <div class="member-role">Uses negotiated market access</div>
                </div>
                <div class="team-member">
                    <div class="member-avatar">AGR</div>
                    <div class="member-name">Agriculture</div>
                    <div class="member-role">Protects politically sensitive rural sectors</div>
                </div>
                <div class="team-member">
                    <div class="member-avatar">MILK</div>
                    <div class="member-name">Dairy Products</div>
                    <div class="member-role">Selective protection inside an open system</div>
                </div>
            </div>
            <img class="deck-figure tariff-figure" src="assets/coral-charts/figure7_tariff_structure_coral.png" alt="Swiss tariff protection by sector">
        </div>

        <!-- Slide 10: Impact of Trump Tariffs -->
        <div class="slide slide-3 with-figure">
            <div class="left-col">
                <div class="number">09</div>
                <div class="col-title">U.S.<br>TARIFFS</div>
            </div>
            <div class="right-col">
                <div class="item">
                    <div class="item-label">Section 232</div>
                    <div class="item-text">The Trump administration imposed tariffs on steel and aluminum, raising trade costs.</div>
                </div>
                <div class="item">
                    <div class="item-label">Swiss Effects</div>
                    <div class="item-text">Reduced metal exports to the United States and increased uncertainty for export industries.</div>
                </div>
                <div class="item">
                    <div class="item-label">Welfare Impact</div>
                    <div class="item-text">Tariffs distort trade flows, reduce efficiency, and hurt small open economies.</div>
                </div>
                <img class="deck-figure tariff-impact-figure" src="assets/coral-charts/figure8_tariff_impact_coral.png" alt="Swiss metal exports to the U.S. after Section 232 tariffs">
            </div>
        </div>

        <!-- Slide 11: Retaliation and Political Economy -->
        <div class="slide slide-6 with-figure political-slide">
            <div class="slide-title">RETALIATION AND POLITICAL ECONOMY</div>
            <div class="slide-subtitle">Small economies often rely on institutions more than direct confrontation</div>
            <div class="columns-grid">
                <div class="column-card">
                    <div class="card-icon">D</div>
                    <div class="card-title">DIPLOMACY</div>
                    <div class="card-text">Switzerland did not pursue aggressive retaliation because it depends heavily on global trade.</div>
                    <div class="card-stat">OPEN</div>
                </div>
                <div class="column-card">
                    <div class="card-icon">W</div>
                    <div class="card-title">WTO</div>
                    <div class="card-text">It favors dispute mechanisms and negotiation to preserve predictable trade relations.</div>
                    <div class="card-stat">RULES</div>
                </div>
                <div class="column-card">
                    <div class="card-icon">B</div>
                    <div class="card-title">BARGAINING</div>
                    <div class="card-text">Limited market size reduces leverage in direct trade confrontation with larger economies.</div>
                    <div class="card-stat">SMALL</div>
                </div>
            </div>
            <img class="deck-figure dependence-figure" src="assets/coral-charts/figure9_trade_dependence_coral.png" alt="Switzerland's dependence on international trade">
        </div>

        <!-- Slide 12: Conclusion -->
        <div class="slide slide-2">
            <div class="section-label">11 / Conclusion</div>
            <div class="big-statement">GLOBALIZATION RAISES INCOME, BUT PROTECTIONISM RAISES RISK</div>
            <div class="body-text">
                Switzerland's trade success is based on innovation and human capital. Comparative advantage explains
                high-value specialization, economies of scale strengthen global competitiveness, and globalization
                creates unequal effects across sectors and workers. U.S. tariffs increased uncertainty for Swiss exports.
            </div>
            <div class="accent-line"></div>
        </div>

        <!-- Slide 13: References -->
        <div class="slide slide-10">
            <div class="left-panel">
                <div class="closing-title">REFER<br>ENCES</div>
                <div class="closing-subtitle">Data sources and textbook foundation for the trade theory analysis.</div>
                <svg class="zigzag-deco" viewBox="0 0 400 60" preserveAspectRatio="none">
                    <path d="M0,30 L40,10 L80,30 L120,10 L160,30 L200,10 L240,30 L280,10 L320,30 L360,10 L400,30 L400,60 L0,60 Z" fill="black"/>
                </svg>
            </div>
            <div class="right-panel">
                <div class="contact-block">
                    <div class="contact-label">Data Sources</div>
                    <div class="contact-value">WTO / WORLD BANK / UN COMTRADE</div>
                </div>
                <div class="contact-block">
                    <div class="contact-label">Institutions</div>
                    <div class="contact-value">IMF / U.S. INTERNATIONAL TRADE COMMISSION</div>
                </div>
                <div class="contact-block">
                    <div class="contact-label">Textbook</div>
                    <div class="contact-value">KRUGMAN, OBSTFELD &amp; MELITZ</div>
                </div>
                <div class="social-row">
                    <div class="social-icon">WTO</div>
                    <div class="social-icon">IMF</div>
                    <div class="social-icon">KOM</div>
                </div>
            </div>
        </div>
    </div>

    <!-- Navigation -->
    <div class="nav-dots" id="navDots"></div>
    <div class="slide-counter" id="slideCounter">01 / 13</div>
    <div class="nav-arrows" id="navArrows">
        <div class="nav-arrow" id="prevArrow">&#8592;</div>
        <div class="nav-arrow" id="nextArrow">&#8594;</div>
    </div>

    <script>
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;
        let currentSlide = 0;

        const navDotsContainer = document.getElementById('navDots');
        const slideCounter = document.getElementById('slideCounter');
        const prevArrow = document.getElementById('prevArrow');
        const nextArrow = document.getElementById('nextArrow');
        const navArrows = document.getElementById('navArrows');

        // Create dots
        slides.forEach((_, index) => {
            const dot = document.createElement('div');
            dot.className = 'nav-dot' + (index === 0 ? ' active' : '');
            dot.addEventListener('click', () => goToSlide(index));
            navDotsContainer.appendChild(dot);
        });

        const dots = document.querySelectorAll('.nav-dot');

        function updateNav() {
            slides.forEach((slide, index) => {
                slide.classList.toggle('active', index === currentSlide);
            });
            dots.forEach((dot, index) => {
                dot.classList.toggle('active', index === currentSlide);
            });
            slideCounter.textContent = String(currentSlide + 1).padStart(2, '0') + ' / ' + String(totalSlides).padStart(2, '0');

            // Check if current slide has light background for dark nav elements
            const currentSlideEl = slides[currentSlide];
            const isLight = currentSlideEl.classList.contains('slide-2') || 
                           currentSlideEl.classList.contains('slide-4') || 
                           currentSlideEl.classList.contains('slide-6') || 
                           currentSlideEl.classList.contains('slide-8');
            
            dots.forEach(d => d.classList.toggle('dark', isLight));
            slideCounter.classList.toggle('dark', isLight);
            prevArrow.classList.toggle('dark', isLight);
            nextArrow.classList.toggle('dark', isLight);
        }

        function goToSlide(index) {
            if (index >= 0 && index < totalSlides) {
                currentSlide = index;
                updateNav();
            }
        }

        function nextSlide() {
            goToSlide((currentSlide + 1) % totalSlides);
        }

        function prevSlide() {
            goToSlide((currentSlide - 1 + totalSlides) % totalSlides);
        }

        prevArrow.addEventListener('click', prevSlide);
        nextArrow.addEventListener('click', nextSlide);

        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                e.preventDefault();
                nextSlide();
            } else if (e.key === 'ArrowLeft') {
                e.preventDefault();
                prevSlide();
            }
        });

        // Chart.js initialization for Slide 4
        function initChart() {
            const ctx = document.getElementById('growthChart');
            if (!ctx) return;

            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['Pharma', 'Chemicals', 'Machinery', 'Watches', 'Finance', 'Medtech'],
                    datasets: [{
                        label: 'Swiss Productivity Advantage',
                        data: [95, 78, 84, 88, 72, 80],
                        backgroundColor: '#E85D5D',
                        borderColor: '#1A1A1A',
                        borderWidth: 2,
                        borderRadius: 0,
                        borderSkipped: false,
                    }, {
                        label: 'Resource Intensity',
                        data: [30, 45, 42, 28, 20, 35],
                        backgroundColor: '#1A1A1A',
                        borderColor: '#1A1A1A',
                        borderWidth: 2,
                        borderRadius: 0,
                        borderSkipped: false,
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'top',
                            labels: {
                                font: { family: 'Inter', size: 12 },
                                color: '#6B6B6B',
                                usePointStyle: true,
                                pointStyle: 'rect',
                                padding: 20
                            }
                        }
                    },
                    scales: {
                        x: {
                            grid: { display: false },
                            ticks: {
                                font: { family: 'Inter', size: 12 },
                                color: '#6B6B6B'
                            }
                        },
                        y: {
                            border: { display: false },
                            grid: {
                                color: 'rgba(26,26,26,0.08)',
                                drawBorder: false
                            },
                            ticks: {
                                font: { family: 'Inter', size: 11 },
                                color: '#B0B0B0',
                                callback: function(value) { return value + '%'; }
                            }
                        }
                    }
                }
            });
        }

        // Initialize chart after a short delay to ensure canvas is visible
        setTimeout(initChart, 300);

        // Initial nav update
        updateNav();
    </script>
</body>
</html>
