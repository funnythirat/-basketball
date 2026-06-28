<!DOCTYPE html>
<html lang="th">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basketball Shoe Advisor | ระบบแนะนำรองเท้าบาส</title>
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600&display=swap" rel="stylesheet">
    <link rel="icon" type="image / PNG" href="https://shorturl.asia/3EXgB">
    <style>
        * {
            box-sizing: border-box;
            font-family: 'Kanit', sans-serif;
            margin: 0;
            padding: 0;
        }

        body {

            background-color: #ffffff;
            /* พื้นหลังสีเทาอ่อนสว่างแบบมินิมอล */
            color: #babc2d;
            padding: 40px 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-image: -webkit-image-set("https://shorturl.asia/irJaI");
            background-repeat: no-repeat;
            background-size: 100%;
        }

        .container {
            width: 100%;
            max-width: 650px;
            background: #7a7f7d;
            padding: 40px;
            border-radius: 24px;
            /* ขอบมนโค้งมนสวยงามตามภาพ */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04), 0 1px 8px rgba(0, 0, 0, 0.02);
        }

        h1 {
            text-align: center;
            font-size: 26px;
            font-weight: 600;
            color: #000000;
            margin-bottom: 4px;
        }

        .subtitle {
            text-align: center;
            font-size: 16px;
            color: #4b5563;
            margin-bottom: 35px;
            font-weight: 400;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            font-size: 14px;
            font-weight: 500;
            margin-bottom: 6px;
            color: #000000;
        }

        /* ปรับแต่งช่องกรอกให้เหมือนในรูปภาพ */
        select,
        input[type="number"] {
            width: 100%;
            padding: 12px 16px;
            border: 1px solid #e5e7eb;
            border-radius: 10px;
            font-size: 14px;
            color: #4b5563;
            background-color: #fafafa;
            outline: none;
            transition: all 0.2s;
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            /* เพิ่มลูกศรด้านขวา */
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%239ca3af'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 16px center;
            background-size: 16px;
        }

        /* ปรับแต่ง input number เฉพาะส่วนที่ไม่มีลูกศร select */
        input[type="number"] {
            background-image: none;
        }

        select:focus,
        input[type="number"]:focus {
            border-color: #f5f5f5;
            background-color: #c9c869;
        }

        /* ปุ่มสีส้มอิฐตรงตามรูปภาพ */
        button {
            width: 100%;
            background-color: #ebe52e;
            color: rgb(0, 0, 0);
            border: none;
            padding: 14px;
            font-size: 16px;
            font-weight: 500;
            border-radius: 12px;
            cursor: pointer;
            transition: background-color 0.2s;
            margin-top: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
        }

        button:hover {
            background-color: #c84413;
        }

        /* ส่วนผลลัพธ์ */
        .result-section {
            margin-top: 35px;
            border-top: 1px solid #f3f4f6;
            padding-top: 25px;
        }

        .result-title {
            font-size: 14px;
            font-weight: 500;
            color: #000000;
            margin-bottom: 15px;
        }

        /* จัดเรียงการ์ดแบบ Grid แนวนอนตามภาพตัวอย่าง */
        .shoe-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 16px;
        }

        /* สไตล์การ์ดรองเท้าด้านล่างแอป */
        .shoe-card {
            background: #ffffff;
            border: 1px solid #ebddad;
            border-radius: 12px;
            padding: 12px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.02);
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .shoe-img {
            width: 100%;
            height: 100px;
            object-fit: contain;
            margin-bottom: 10px;
        }

        .shoe-name {
            font-size: 13px;
            font-weight: 500;
            color: #111827;
            margin-bottom: 4px;
            line-height: 1.3;
        }

        .shoe-tag {
            font-size: 11px;
            color: #6b7280;
        }

        .no-result {
            text-align: center;
            color: #6b7280;
            padding: 30px 20px;
            background: #f9fafb;
            border-radius: 12px;
            border: 1px dashed #e5e7eb;
            font-size: 14px;
        }

        .buy-btn {
            display: inline-block;
            background-color: #ff5722;
            /* สีส้มสดใสแนวแอปช้อปปิ้ง หรือเปลี่ยนตามธีมเว็บคุณได้เลย */
            color: white;
            text-decoration: none;
            /* เอาเส้นใต้ลิงก์ออก */
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: bold;
            margin-top: 10px;
            transition: background 0.3s ease;
            text-align: center;
        }

        .buy-btn:hover {
            background-color: #e64a19;
            /* สีจะเข้มขึ้นเวลคุมเมาส์ (Hover) */
            color: white;
        }

        .shoe-rating {
            margin-top: 8px;
            margin-bottom: 4px;
            font-size: 14px;
            text-align: center;
        }

        .shoe-rating .stars {
            color: #ffca28;
            /* สีเหลืองทองของดาว */
        }

        .shoe-rating .rating-text {
            color: #666;
            /* สีเทาสำหรับตัวเลขคะแนน */
            font-weight: bold;
            margin-left: 4px;
        }
    </style>
</head>

<body>
    <div class="container">
        <h1>Basketball Shoe Advisor</h1>
        <p class="subtitle">ระบบแนะนำรองเท้าบาส</p>
        <div class="form-group">
            <label for="position">1. ตำแหน่งที่เล่น (Position)</label>
            <select id="position">
                <option value="PG">Point Guard (PG)</option>
                <option value="SG">Shooting Guard (SG)</option>
                <option value="SF">Small Forward (SF)</option>
                <option value="PF">Power Forward (PF)</option>
                <option value="C">Center (C)</option>
            </select>
        </div>
        <div class="form-group">
            <label for="style">2. สไตล์การเล่นหลัก (Play Style)</label>
            <select id="style">
                <option value="สายสปีด">สายสปีด / ความคล่องตัวสูง</option>
                <option value="ชู้ตเตอร์">ชู้ตเตอร์ / วิ่งหาที่ว่างยิง</option>
                <option value="เน้นกระโดด">เน้นกระโดด / รีบาวด์ / บล็อก</option>
                <option value="พละกำลัง">พละกำลัง / สายลุยปะทะ</option>
                <option value="การ์ดโดยเฉพาะ">การ์ดจ่าย </option>
            </select>
        </div>
        <div class="form-group">
            <label for="size">3. ไซส์รองเท้าของคุณ (US)</label>
            <input type="number" id="size" step="0.5" min="7" max="15" value="10.0">
        </div>
        <button onclick="recommendShoes()">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"
                stroke-linecap="round" stroke-linejoin="round">
                <circle cx="11" cy="11" r="8"></circle>
                <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
            </svg>
            ค้นหารองเท้าของฉัน
        </button>
        <div class="result-section" id="resultArea" style="display: none;">
            <div class="result-title" id="resultCount">result-section</div>
            <div class="shoe-grid" id="resultContainer"></div>
        </div>
    </div>
    <script>
        // คลังข้อมูลรองเท้าบาสเกตบอล (Database - แก้ไขคำผิดและทำความสะอาดข้อมูลแล้ว)
        const shoeDatabase = [
            {
                name: "Li-Ning Wade All City 12",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "เน้นกระโดด", "ชู้ตเตอร์"],
                sizes: [8.0, 9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Wade-style",
                image: "https://shorturl.asia/LJQyS",
                shopUrl: "https://shorturl.asia/4wGaA",
                rating: 4.8

            },
            {
                name: "Nike Ja 1",
                positions: ["PG", "SF", "SG", "PF", "C"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Ja-shoes",
                image: "https://shorturl.asia/VmNF9",
                shopUrl: "https://shorturl.asia/UQ3EN",
                rating: 5.0

            },
            {
                name: "Nike LeBron 19",
                positions: ["C", "SF", "PF"],
                styles: ["สายสปีด", "พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Lebron-style",
                image: "https://shorturl.asia/pNXDx",
                shopUrl: "https://shorturl.asia/nLwgi",
                rating: 3.8
            },
            {
                name: "Xtep Jlin 3",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Jlin-shoes",
                image: "https://shorturl.asia/s7g4e",
                shopUrl: "https://shorturl.asia/28bpF",
                rating: 4.5
            },
            {
                name: "Anta Kai 1",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Kai-shoes",
                image: "https://shorturl.asia/Y5pZS",
                shopUrl: "https://shorturl.asia/nkbdB",
                rating: 4.8
            },
            {
                name: "nike lebron 20",
                positions: ["SF", "PF", "C"],
                styles: ["พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Lebron-style",
                image: "https://shorturl.asia/U0mD5",
                shopUrl: "https://shorturl.asia/fli0j",
                rating: 4.9
            },
            {
                name: "Nike Kobe 6 Protro",
                positions: ["PG", "SG", "SF"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [8.5, 9.0, 9.5, 10.0, 10.5],
                tag: "Kobe-style",
                image: "https://shorturl.asia/IoVA3",
                shopUrl: "https://shorturl.asia/t3r2q",
                rating: 5.0
            },
            {
                name: "Adidas Harden Vol.7",
                positions: ["PG", "SG"],
                styles: ["สายสปีด", "พละกำลัง"],
                sizes: [9.5, 10.0, 10.5, 11.0, 11.5],
                tag: "Harden-shoes",
                image: "https://shorturl.asia/NWojY",
                shopUrl: "https://shorturl.asia/phrBR",
                rating: 4.4
            },
            {
                name: "Under Armour Curry 10",
                positions: ["PG", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [8.0, 8.5, 9.0, 9.5, 10.0, 10.5, 11.0],
                tag: "Curry-style",
                image: "https://bit.ly/4frUO5s",
                shopUrl: "https://shorturl.asia/e9Xq8",
                rating: 5.0
            },
            {
                name: "Air Jordan 38",
                positions: ["SF", "PF", "C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [10.0, 10.5, 11.0, 11.5, 12.0, 13.0],
                tag: "Jordan-shoes",
                image: "https://shorturl.asia/tZWd3",
                shopUrl: "https://shorturl.asia/QyiCh",
                rating: 3.8
            },
            {
                name: "361° DVD 1",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "DVD-shoes",
                image: "https://shorturl.asia/ABMgl",
                shopUrl: "https://shorturl.asia/CpWPX",
                rating: 4.3
            },
            {
                name: "Li-Ning Sonic 11",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด"],
                sizes: [8.0, 9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Sonic-style",
                image: "https://shorturl.asia/0IegS",
                shopUrl: "https://shorturl.asia/C5G3m",
                rating: 4.5
            },
            {
                name: "Li-Ning Way of Wade Flash",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด"],
                sizes: [8.0, 9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Wade-style",
                image: "https://shorturl.asia/rKYex",
                shopUrl: "https://shorturl.asia/cOUNi",
                rating: 4.4
            },
            {
                name: "Li-Ning Gamma",
                positions: ["PG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "การ์ดโดยเฉพาะ"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Gamma-style",
                image: "https://shorturl.asia/RUzt2",
                shopUrl: "https://shorturl.asia/QVucL",
                rating: 4.3
            },
            {
                name: "Anta Shock Wave 5",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "ShockWave-style",
                image: "https://shorturl.asia/bfRq2",
                shopUrl: "https://shorturl.asia/iwc2q",
                rating: 4.9
            },
            {
                name: "Anta Shock Wave 6",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "ShockWave-style",
                image: "https://shorturl.asia/Y6NOe",
                shopUrl: "https://shorturl.asia/BJYgW",
                rating: 4.8
            },
            {
                name: "361° DVD 2",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "DVD-shoes",
                image: "https://shorturl.asia/ButaU",
                shopUrl: "https://shorturl.asia/iJksy",
                rating: 4.5
            },
            {
                name: "Rigorer AR1",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "AustinReaves-style",
                image: "https://shorturl.asia/ButaU",
                shopUrl: "https://shorturl.asia/lkQSH",
                rating: 4.7
            },
            {
                name: "Nike LeBron NXXT Gen",
                positions: ["PF", "SF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Lebron-style",
                image: "https://shorturl.asia/NHv7F",
                shopUrl: "https://shorturl.asia/5ZK8P",
                rating: 4.6
            },
            {
                name: "Nike KD 16",
                positions: ["PF", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "KD-style",
                image: "https://shorturl.asia/98K4q",
                shopUrl: "https://shorturl.asia/htpTY",
                rating: 4.4
            },
            {
                name: "Nike KD 17",
                positions: ["PF", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "KD-style",
                image: "https://shorturl.asia/5VksW",
                shopUrl: "https://shorturl.asia/TD7eA",
                rating: 4.4
            },
            {
                name: "Nike Giannis Immortality 3",
                positions: ["PF", "SF", "C"],
                styles: ["เน้นกระโดด", "สายสปีด", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Giannis-style",
                image: "https://shorturl.asia/xvgyK",
                shopUrl: "https://shorturl.asia/sSDpF",
                rating: 4.0
            },
            {
                name: "Nike Giannis Immortality 4",
                positions: ["PF", "SF", "SG"],
                styles: ["สายสปีด", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Giannis-style",
                image: "https://shorturl.asia/lMk56",
                shopUrl: "https://shorturl.asia/xOzjg",
                rating: 4.0
            },
            {
                name: "Jordan Zion 3",
                positions: ["PF", "SF", "C"],
                styles: ["สายสปีด", "เน้นกระโดด", "สายลุยปะทะ"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Zion-style",
                image: "https://shorturl.asia/hWO9p",
                shopUrl: "https://shorturl.asia/2epBf",
                rating: 4.0
            },
            {
                name: "Jordan One Take 4",
                positions: ["SF", "SG"],
                styles: ["สายสปีด", "พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Westbrook-style",
                image: "https://shorturl.asia/rUmYi",
                shopUrl: "https://shorturl.asia/BLA09",
                rating: 4.1
            },
            {
                name: "adidas BYW Select",
                positions: ["SF", "SG"],
                styles: ["สายสปีด", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "adidas-basketball",
                image: "https://shorturl.asia/0b4gU",
                shopUrl: "https://shorturl.asia/bQXgx",
                rating: 4.2
            },
            {
                name: "Puma MB.03",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Melo-style",
                image: "https://shorturl.asia/l4gVe",
                shopUrl: "https://shorturl.asia/CoaOz",
                rating: 4.0
            },
            {
                name: "Puma MB.04",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Melo-style",
                image: "https://shorturl.asia/2bKs0",
                shopUrl: "https://shorturl.asia/mbYsy",
                rating: 4.0
            },
            {
                name: "Puma Rise Nitro",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Puma-style",
                image: "https://shorturl.asia/TlE8v",
                shopUrl: "https://shorturl.asia/UNMeb   ",
                rating: 1.0
            },
            {
                name: "ASICS Gelburst 27",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Asics-style",
                image: "https://shorturl.asia/mlNqL",
                shopUrl: "https://shorturl.asia/R6n4m",
                rating: 4.1
            },
            {
                name: "ASICS Gelburst 28",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Asics-style",
                image: "https://shorturl.asia/65gYy",
                shopUrl: "https://shorturl.asia/6bZ1M",
                rating: 4.8
            },
            {
                name: "ASICS Nova Surge Low",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Asics-style",
                image: "https://shorturl.asia/u7BJY",
                shopUrl: "https://shorturl.asia/YSc9X",
                rating: 4.6
            },
            {
                name: "Li-Ning Wade Shadow 5",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Wade-style",
                image: "https://shorturl.asia/aXDBh",
                shopUrl: "https://shorturl.asia/SmH7O",
                rating: 4.4
            },
            {
                name: "Li-Ning Fission 9",
                positions: ["PG", "SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Wade-style",
                image: "https://shorturl.asia/r4JBU",
                shopUrl: "https://shorturl.asia/Rt6sc",
                rating: 4.8
            },
            {
                name: "Nike Air Max Impact 4",
                positions: ["PF", "SF", "C"],
                styles: ["เน้นกระโดด", "พละกำลัง", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Nike-style",
                image: "https://shorturl.asia/iW9Xl",
                shopUrl: "https://shorturl.asia/LJiBO",
                rating: 4.6
            },
            {
                name: "Jordan 39",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "ชู้ตเตอร์", "พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Jordan-shoes",
                image: "https://shorturl.asia/UZ9gF",
                shopUrl: "https://shorturl.asia/TCFif",
                rating: 4.0
            },
            {
                name: "Nike Air Zoom G.T. Hustle 3",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "GT-Series",
                image: "https://shorturl.asia/7J5TI",
                shopUrl: "https://shorturl.asia/cnVDX",
                rating: 4.2
            },
            {
                name: "Nike Air Zoom G.T. Hustle 2",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "GT-Series",
                image: "https://shorturl.asia/Efb0h",
                shopUrl: "https://shorturl.asia/UcdFZ",
                rating: 4.0
            },
            {
                name: "Nike LeBron 21",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "สายลุยปะทะ", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Lebron-style",
                image: "https://shorturl.asia/r5zN4",
                shopUrl: "https://shorturl.asia/b8E6s",
                rating: 4.7
            },
            {
                name: "Nike Air Zoom G.T. Jump 2",
                positions: ["PF", "SF", "C"],
                styles: ["สายสปีด", "เน้นกระโดด", "สายลุยปะทะ"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "GT-Series",
                image: "https://shorturl.asia/N5AcL",
                shopUrl: "https://shorturl.asia/8urk1",
                rating: 4.2
            },
            {
                name: "Rigorer Sniper 2",
                positions: ["SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/mrBFf",
                shopUrl: "https://shorturl.asia/eyPpw",
                rating: 4.2
            },
            {
                name: "361° Zen 6",
                positions: ["SG", "SF"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Zen-style",
                image: "https://shorturl.asia/yM2KB",
                shopUrl: "https://shorturl.asia/s0VLA",
                rating: 4.6
            },
            {
                name: "361° Zen 5",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Zen-style",
                image: "https://shorturl.asia/wQus1",
                shopUrl: "https://shorturl.asia/zlAaq",
                rating: 4.5
            },
            {
                name: "Anta KT 8",
                positions: ["SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Thompson-style",
                image: "https://shorturl.asia/dfiuF",
                shopUrl: "https://shorturl.asia/X6MQ2",
                rating: 4.2
            },
            {
                name: "Anta KT 9",
                positions: ["SF", "SG"],
                styles: ["สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Thompson-style",
                image: "https://shorturl.asia/U289x",
                shopUrl: "https://shorturl.asia/05zWL",
                rating: 4.5
            },
            {
                name: "Nike Giannis Freak 5",
                positions: ["PF", "C"],
                styles: ["เน้นกระโดด", "สายสปีด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Freak-style",
                image: "https://shorturl.asia/VuvKp",
                shopUrl: "https://shorturl.asia/KAd9k",
                rating: 4.4
            },
            {
                name: "Nike Giannis Freak 6",
                positions: ["PF", "C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Freak-style",
                image: "https://shorturl.asia/uXFvJ",
                shopUrl: "https://shorturl.asia/KAd9k",
                rating: 4.5
            },
            {
                name: "Jordan Jumpman MVP",
                positions: ["C", "PF"],
                styles: ["สายสปีด", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Jordan-shoes",
                image: "https://shorturl.asia/W5K1M",
                shopUrl: "https://shorturl.asia/VwnLl",
                rating: 4.1
            },
            {
                name: "adidas Mad Bounce",
                positions: ["PF"],
                styles: ["พละกำลัง", "สายสปีด", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "adidas-basketball",
                image: "https://shorturl.asia/tF8T2",
                shopUrl: "https://shorturl.asia/gIzwy",
                rating: 4.5
            },
            {
                name: "Li-Ning Badfive 2",
                positions: ["PF", "SF"],
                styles: ["เน้นกระโดด", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Badfive-style",
                image: "https://shorturl.asia/taZU3",
                shopUrl: "https://shorturl.asia/r0AjG",
                rating: 4.5
            },
            {
                name: "Li-Ning Sonic 12",
                positions: ["SG", "PF"],
                styles: ["เน้นกระโดด", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Sonic-style",
                image: "https://shorturl.asia/ijm6B",
                shopUrl: "https://shorturl.asia/CIOo7",
                rating: 4.6
            },
            {
                name: "Anta Gordon Hayward 3",
                positions: ["PF"],
                styles: ["เน้นกระโดด", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Hayward-style",
                image: "https://shorturl.asia/QD6mo",
                shopUrl: "https://shorturl.asia/JOrDl",
                rating: 4.3
            },
            {
                name: "361° Big 3 5.0 Quick",
                positions: ["PF", "SF"],
                styles: ["เน้นกระโดด", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Big3-style",
                image: "https://shorturl.asia/6ujv5",
                shopUrl: "https://shorturl.asia/zylOD",
                rating: 4.4
            },
            {
                name: "361° AG3",
                positions: ["PF"],
                styles: ["เน้นบล็อก", "พละกำลัง", "เน้นกระโดด", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "AaronGordon-style",
                image: "https://shorturl.asia/g9MB1",
                shopUrl: "https://shorturl.asia/ovpRf",
                rating: 4.6
            },
            {
                name: "Peak Taichi Big Triangle 4.0",
                positions: ["PF", "SF"],
                styles: ["สายสปีด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Peak-style",
                image: "https://shorturl.asia/1N8bq",
                shopUrl: "https://shorturl.asia/VCm28",
                rating: 4.7
            },
            {
                name: "Peak Flash 4.0",
                positions: ["PF"],
                styles: ["พละกำลัง", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Peak-style",
                image: "https://shorturl.asia/7CW5w",
                shopUrl: "https://shorturl.asia/xUnv3",
                rating: 4.4
            },
            {
                name: "Rigorer Sniper 1",
                positions: ["PF"],
                styles: ["พละกำลัง", "เน้นบล็อก", "สายป้องกัน"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/Fv8si",
                shopUrl: "https://shorturl.asia/3Wzo5",
                rating: 4.3
            },
            {
                name: "Nike Air Max Impact 3",
                positions: ["C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Nike-style",
                image: "https://shorturl.asia/zPGa1",
                shopUrl: "https://shorturl.asia/YT0Vw",
                rating: 4.5
            },
            {
                name: "Nike LeBron Witness 7",
                positions: ["PF", "C"],
                styles: ["สายป้องกัน", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Witness-style",
                image: "https://shorturl.asia/95O47",
                shopUrl: "https://shorturl.asia/bVuOm",
                rating: 4.0
            },
            {
                name: "Nike LeBron Witness 8",
                positions: ["PF", "C"],
                styles: ["เน้นกระโดด", "พละกำลัง", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Witness-style",
                image: "https://shorturl.asia/kdQKY",
                shopUrl: "https://shorturl.asia/yjreq",
                rating: 4.2
            },
            {
                name: "adidas Pro Bounce 2019",
                positions: ["C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "adidas-basketball",
                image: "https://shorturl.asia/HpDor",
                shopUrl: "https://shorturl.asia/1xYDk",
                rating: 4.8
            },
            {
                name: "adidas Marquee Boost High",
                positions: ["C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "adidas-basketball",
                image: "https://shorturl.asia/AmhEP",
                shopUrl: "https://shorturl.asia/U2lAv",
                rating: 4.4
            },
            {
                name: "Li-Ning YuShuai 16",
                positions: ["C"],
                styles: ["พละกำลัง", "รีบาวด์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "YuShuai-style",
                image: "https://shorturl.asia/8T2qx",
                shopUrl: "https://shorturl.asia/2yY6t",
                rating: 4.7
            },
            {
                name: "Li-Ning Dominator",
                positions: ["C", "PF"],
                styles: ["พละกำลัง", "เน้นบล็อก"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Li-Ning-style",
                image: "https://shorturl.asia/CnYQk",
                shopUrl: "https://shorturl.asia/cTHvJ",
                rating: 4.6
            },
            {
                name: "Anta KT 7",
                positions: ["C", "SG"],
                styles: ["ชู้ตเตอร์", "พละกำลัง", "รีบาวด์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Thompson-style",
                image: "https://shorturl.asia/5iEWZ",
                shopUrl: "https://shorturl.asia/loY3H",
                rating: 4.7
            },
            {
                name: "361° Zen 4",
                positions: ["C", "PF"],
                styles: ["พละกำลัง", "เน้นกระโดด", "รีบาวด์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Zen-style",
                image: "https://shorturl.asia/lPNv9",
                shopUrl: "https://shorturl.asia/sn7Yj",
                rating: 4.4
            },
            {
                name: "Peak Streetball Master 2",
                positions: ["C"],
                styles: ["รีบาวด์", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Peak-style",
                image: "https://shorturl.asia/S6WxL",
                shopUrl: "https://shorturl.asia/5cy9T",
                rating: 4.8
            },
            {
                name: "Peak Dwight Howard 3",
                positions: ["C"],
                styles: ["เน้นกระโดด", "พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Howard-style",
                image: "https://shorturl.asia/fFeRA",
                shopUrl: "https://shorturl.asia/cq97o",
                rating: 4.6
            },
            {
                name: "Xtep Jlin 2 SE",
                positions: ["PF", "C"],
                styles: ["พละกำลัง", "เน้นกระโดด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Jlin-shoes",
                image: "https://shorturl.asia/9uiGo",
                shopUrl: "https://shorturl.asia/IVAtU",
                rating: 4.5
            },
            {
                name: "Nike Air Zoom G.T. Cut 3",
                positions: ["C", "PF"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/bS5z4",
                shopUrl: "https://shorturl.asia/H5u2k",
                rating: 4.4
            },
            {
                name: "Jordan Jumpman Two Three",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์", "เน้นพละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/Okf4K",
                shopUrl: "https://shorturl.asia/gOec1",
                rating: 4.3
            },
            {
                name: "adidas Dame 7 Extply",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/KWASH",
                shopUrl: "https://shorturl.asia/hbmgE",
                rating: 4.7
            },
            {
                name: "adidas Adizero Select 2.0",
                positions: ["C", "PF"],
                styles: ["เน้นกระโดด", "สายสปีด"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/WTZU1",
                shopUrl: "https://shorturl.asia/indyx",
                rating: 4.4
            },
            {
                name: "adidas D Rose Son of Chi 3",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/Wi0K4",
                shopUrl: "https://shorturl.asia/2R0rd",
                rating: 5.0
            },
            {
                name: "Under Armour Spawn 5",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/CecVU",
                shopUrl: "https://shorturl.asia/L6gnP",
                rating: 4.1
            },
            {
                name: "Puma Stewie 2",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/hVs1w",
                shopUrl: "https://shorturl.asia/SJt6B",
                rating: 4.5
            },
            {
                name: "Puma TRC Blaze Court",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/CwVEu",
                shopUrl: "https://shorturl.asia/VWBHP",
                rating: 4.1
            },
            {
                name: "Li-Ning Wade All City 11 V2",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/tYR6B",
                shopUrl: "https://shorturl.asia/Gr3FJ",
                rating: 4.8
            },
            {
                name: "Li-Ning Wade Shadow 4",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/NyTJt",
                shopUrl: "https://shorturl.asia/FLDiB",
                rating: 4.3
            },
            {
                name: "Li-Ning Speed 10",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/EZCbU",
                shopUrl: "https://shorturl.asia/4DVQX",
                rating: 4.6
            },
            {
                name: "Anta Shock Wave 5 Lite",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/0rpZt",
                shopUrl: "https://shorturl.asia/yELHD",
                rating: 4.7
            },
            {
                name: "Anta Skyline 2",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/8h1SU",
                shopUrl: "https://shorturl.asia/gfwq4",
                rating: 4.5
            },
            {
                name: "Anta KT Splash 5",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/kEzb8",
                shopUrl: "https://shorturl.asia/gfwq4",
                rating: 4.6
            },
            {
                name: "361° Big 3 4.0 Quick",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/TvdA6",
                shopUrl: "https://shorturl.asia/NxYje",
                rating: 4.5
            },
            {
                name: "361° DVD 1 SE",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/qET7x",
                shopUrl: "https://shorturl.asia/IaB17",
                rating: 4.4
            },
            {
                name: "Peak Taichi Flash 4.0",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/7CW5w",
                shopUrl: "https://shorturl.asia/H1OUE",
                rating: 4.5
            },
            {
                name: "Peak Soaring II",
                positions: ["C", "PF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/sch2X",
                shopUrl: "https://shorturl.asia/caN9f",
                rating: 4.4
            },
            {
                name: "nike gt cut 3",
                positions: ["PG", "SF", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์","พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/15m2u",
                shopUrl: "https://shorturl.asia/Cmt28",
                rating: 5.0
            },
            {
                name: "Nike Air Zoom G.T. Cut 2",
                positions: ["SF", "PG", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์","พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/buxm8",
                shopUrl: "https://shorturl.asia/BEcz3",
                rating: 4.4
            },
            {
                name: "Nike Air Zoom G.T. Cut acdemy",
                positions: ["SF", "PG", "SG"],
                styles: ["เน้นกระโดด", "สายสปีด", "ชู้ตเตอร์","พละกำลัง"],
                sizes: [9.0, 9.5, 10.0, 10.5, 11.0, 12.0],
                tag: "Rigorer-style",
                image: "https://shorturl.asia/qV9hc",
                shopUrl: "https://shorturl.asia/FyNg2",
                rating: 4.7
            },
        ];

        function recommendShoes() {
            const userPosition = document.getElementById('position').value.trim().toUpperCase();
            const userStyle = document.getElementById('style').value.trim();
            const userSize = parseFloat(document.getElementById('size').value);

            const resultArea = document.getElementById('resultArea');
            const resultContainer = document.getElementById('resultContainer');
            const resultCount = document.getElementById('resultCount');

            resultContainer.innerHTML = "";
            resultArea.style.display = "block";

            const recommendedShoes = shoeDatabase.filter(shoe => {
                const posMatch = shoe.positions.map(p => p.trim().toUpperCase()).includes(userPosition);
                const styleMatch = shoe.styles.map(s => s.trim()).includes(userStyle);
                const sizeMatch = shoe.sizes.includes(userSize);
                return posMatch && styleMatch && sizeMatch;
            });

            if (recommendedShoes.length > 0) {
                resultCount.textContent = `ผลลัพธ์ที่แนะนำ (${recommendedShoes.length} รุ่น):`;
                let htmlContent = "";

                recommendedShoes.forEach(shoe => {
                    const currentShopUrl = shoe.shopUrl ? shoe.shopUrl : "#";

                    // สร้างข้อความคะแนนและดาวรีวิว (ถ้าไม่มีข้อมูลให้ใส่เป็น N/A หรือ 0)
                    const shoeRating = shoe.rating ? shoe.rating : 0;
                    const stars = "⭐".repeat(Math.round(shoeRating)); // แปลงคะแนนเป็นจำนวนดาวแบบปัดเศษ
                    htmlContent += `
                <div class="shoe-card">
                    <img src="${shoe.image}" alt="${shoe.name}" class="shoe-img" onerror="this.src='https://placehold.co/100x100?text=No+Image'">    
                    <!-- ส่วนแสดงคะแนนรีวิวใต้ภาพ -->
                    <div class="shoe-rating">
                        <span class="stars">${stars}</span> 
                        <span class="rating-text">(${shoeRating}/5)</span>
                    </div>
                    <div class="shoe-name">${shoe.name}</div>
                    <div class="shoe-tag">${shoe.tag}</div>
                    <a href="${currentShopUrl}" target="_blank" class="buy-btn">
                        🛒 ไปที่ร้านค้า
                    </a>
                </div>
            `;
                });
                resultContainer.innerHTML = htmlContent;
            } else {
                resultCount.textContent = "ผลลัพธ์:";
                resultContainer.innerHTML = `
            <div class="no-result" style="grid-column: 1 / -1;">
                <p>😢 ไม่พบรองเท้าที่ตรงเงื่อนไขของคุณ</p>
            </div>
        `;
            }
        }
    </script>
</body>

</html>
