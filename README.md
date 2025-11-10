<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vòng Xoay Kinh Dịch – Thiên Địa Nhân</title>
    <style>
      body {
        background-color: #0d0d0d;
        color: #e0e0b0;
        font-family: "Noto Serif", "Times New Roman", serif;
        text-align: center;
        padding: 30px;}
    h1 {
        color: #ffd700;
        letter-spacing: 2px;
        text-shadow: 0 0 8px #ffcc00;}
    .vong-xoay {
        margin: 20px auto;
        width: 200px;
        height: 200px;
        border-radius: 50%;
        border: 3px solid #888;
        background: radial-gradient(circle, #222 30%, #000);
        display: flex;
        align-items: center;
        justify-content: center;
        color: #66ffcc;
        font-size: 18px;
        box-shadow: 0 0 20px #333 inset;
        transition: transform 2s ease-out;}
    .nut {
        background: linear-gradient(90deg, #444, #222);
        border: 1px solid #999;
        color: #ffd700;
        font-size: 18px;
        padding: 10px 20px;
        cursor: pointer;
        border-radius: 12px;
        margin-top: 20px;
        box-shadow: 0 0 10px #666;}
    .nut:hover {
        background: linear-gradient(90deg, #555, #333);
        color: #fff;}
    .ketqua {
        margin-top: 30px;
        border-top: 1px solid #777;
        padding-top: 20px;}
    .tenque {
        font-size: 24px;
        color: #ffdd55;
        margin-bottom: 10px;}
    .bieuhao {
        font-size: 28px;
        color: #99ffcc;
        margin-bottom: 10px;}
    .loigiai {
        font-size: 17px;
        color: #cccccc;
        font-style: italic;}
    </style>
  </head>
  <body>
<h1>⚛️ VÒNG XOAY KINH DỊCH ⚛️<br><small>Thiên – Địa – Nhân – Âm – Dương</small></h1>
<div id="vong" class="vong-xoay">Âm – Dương</div>
<button id="xoay" class="nut">Xoay Vòng</button>
<div class="ketqua" id="ketqua">
    <div class="tenque">Hãy xoay để xem quẻ...</div>
</div>
<script>
// Danh sách 64 quẻ (rút gọn còn 10 quẻ làm mẫu, có thể mở rộng đủ 64)
const dsQue = [
    {ten:"乾 Qián (Càn)", bieuHao:"☰ ☰ ☰", loiGiai:"Quẻ Càn biểu hiện nguyên khí trời, Thiên dẫn Địa sinh, Âm nhuần Dương, mở nguồn lực sáng tạo."},
    {ten:"坤 Kūn (Khôn)", bieuHao:"☷ ☷ ☷", loiGiai:"Quẻ Khôn biểu đất bao dung, Địa nhiếp Thiên, Dương tĩnh Âm động, nhận dưỡng vạn vật."},
    {ten:"屯 Zhūn (Trùng Khởi)", bieuHao:"☳ ☵ ☳", loiGiai:"Khởi đầu gian khó như mầm non đâm chồi, Âm-Dương hỗ hoà, cần nhẫn nại và lập chí."},
    {ten:"蒙 Méng (Mông)", bieuHao:"☵ ☳ ☳", loiGiai:"Quẻ Mông như trẻ non học hỏi, thiên địa ban hướng, trí tuệ cần khai mở."},
    {ten:"需 Xū (Ngự)", bieuHao:"☰ ☵ ☷", loiGiai:"Quẻ Ngự gặp nguy mà giữ chính, Thiên Địa vẹn hòa, người quân tử tỉnh thức."},
    {ten:"师 Shī (Sư)", bieuHao:"☳ ☷ ☳", loiGiai:"Quẻ Sư như đội quân hành quân, chuẩn bị kỹ lưỡng trước khi phát khởi."},
    {ten:"泰 Tài (Thái)", bieuHao:"☷ ☰ ☰", loiGiai:"Quẻ Thái thời thuận lợi lớn, Thiên Địa hoà hợp, nhân vận hanh thông."},
    {ten:"否 Pǐ (Bĩ)", bieuHao:"☰ ☷ ☷", loiGiai:"Quẻ Bĩ thời thế nghịch, Dương bị Âm che, cần giữ chí hướng."},
    {ten:"同人 Tóng Rén (Đồng Nhân)", bieuHao:"☰ ☷ ☰", loiGiai:"Quẻ Đồng Nhân nhân bản tương giao, người hợp tác tạo nên vũ khí chí thiện."},
    {ten:"大有 Dà Yǒu (Đại Hữu)", bieuHao:"☰ ☰ ☷", loiGiai:"Quẻ Đại Hữu thịnh vượng, tích hoạch thành quả, nhưng cần khiêm nhường."}];
const vong = document.getElementById("vong");
const nut = document.getElementById("xoay");
const ketqua = document.getElementById("ketqua");
nut.addEventListener("click", () => {
    // Tạo hiệu ứng xoay vòng
    const goc = 360 * 3 + Math.floor(Math.random() * 360);
    vong.style.transform = `rotate(${goc}deg)`;
 // Sau khi xoay xong, hiển thị quẻ
    setTimeout(() => {
        const idx = Math.floor(Math.random() * dsQue.length);
        const q = dsQue[idx];
        ketqua.innerHTML = `
            <div class="tenque">${q.ten}</div>
            <div class="bieuhao">${q.bieuHao}</div>
            <div class="loigiai">${q.loiGiai}</div>`;}, 2000);});
</script>
</body>
</html>
