// -*- coding: utf‑8 -*-
// Chương trình “Vòng Xoay Kinh Dịch” – phong cách huyền học, Âm‑Dương, Thiên‑Địa‑Nhân  
// Ngôn ngữ: C++11 trở lên  
#include <iostream>
#include <string>
#include <vector>
#include <cstdlib>   // for rand(), srand()
#include <ctime>     // for time()
#ifdef _WIN32
#include <windows.h> // để đổi màu console nếu là Windows
#endif

struct Que {
    std::string ten;
    std::string bieuHao;
    std::string loiGiai;};

std::vector<Que> dsQue = {
    { "乾 Qián (Càn)", "☰ ☰ ☰", "Quẻ Càn biểu hiện nguyên khí trời, Thiên dẫn Địa sinh, Âm nhuần Dương, mở nguồn lực sáng tạo." },
    { "坤 Kūn (Khôn)", "☷ ☷ ☷", "Quẻ Khôn biểu đất bao dung, Địa nhiếp Thiên, Dương tĩnh Âm động, nhận dưỡng vạn vật." },
    { "屯 Zhūn (Trùng Khởi)", "☳ ☵ ☳", "Khởi đầu gian khó như mầm non đâm chồi, Âm‑Dương hỗ hoà, cần nhẫn nại và lập chí." },
    { "蒙 Méng (Mông)", "☵ ☳ ☳", "Quẻ Mông như trẻ non học hỏi, thiên địa ban hướng, trí tuệ cần khai mở." },
    { "需 Xū (Ngự)", "☰ ☵ ☷", "Quẻ Ngự gặp nguy mà giữ chính, Thiên Địa vẹn hòa, người quân tử tỉnh thức." },
    { "讼 Sòng (Tụng)", "☷ ☵ ☰", "Quẻ Tụng phản ánh xung đột, Âm Dương giao tranh, phải dùng lễ nhẫn để hoà giải." },
    { "师 Shī (Sư)", "☳ ☷ ☳", "Quẻ Sư như đội quân hành quân, chuẩn bị kỹ lưỡng trước khi phát khởi." },
    { "比 Bǐ (Tỷ)", "☳ ☷ ☷", "Quẻ Tỷ đồng minh tương trợ, Thiên đất đồng hành, sức mạnh cộng hưởng." },
    { "小畜 Xiǎo Xù (Tiểu Súc)", "☰ ☳ ☰", "Quẻ Tiểu Súc tích trữ tiềm năng nhỏ, ẩn nhẫn chờ thời." },
    { "履 Lǚ (Lộ)", "☷ ☰ ☷", "Quẻ Lộ tiến hành trên đất vững, từng bước chắc chắn, không vội vàng." },
    { "泰 Tài (Thái)", "☷ ☰ ☰", "Quẻ Thái thời thuận lợi lớn, Thiên Địa hoà hợp, nhân vận hanh thông." },
    { "否 Pǐ (Bĩ)", "☰ ☷ ☷", "Quẻ Bĩ thời thế nghịch, Dương bị Âm che, cần giữ chí hướng." },
    { "同人 Tóng Rén (Đồng Nhân)", "☰ ☷ ☰", "Quẻ Đồng Nhân nhân bản tương giao, người hợp tác tạo nên vũ khí chí thiện."},
    { "大有 Dà Yǒu (Đại Hữu)", "☰ ☰ ☷", "Quẻ Đại Hữu thịnh vượng, tích hoạch thành quả, nhưng cần khiêm nhường." },
    { "谦 Qiān (Khiêm)", "☷ ☷ ☰", "Quẻ Khiêm giữ mình thấp để người khác tiến, Âm hỗ Dương biến." },
    { "豫 Yù (Dự)", "☷ ☰ ☷", "Quẻ Dự vui mừng trước sự tới, Thiên Địa đồng hưởng, nên xả tâm chờ vận." },
    { "随 Suí (Tùy)", "☰ ☷ ☵", "Quẻ Tùy thuận hoàn cảnh như nước chảy, uyển chuyển theo thiên thời." },
    { "蛊 Gǔ (Cổ)", "☵ ☷ ☰", "Quẻ Cổ thanh lọc, quay trở lại cội nguồn, người sửa mình trước khi sửa khác." },
    { "临 Lín (Lâm)", "☷ ☷ ☳", "Quẻ Lâm đến gần, dẫn dắt người khác, giữ nhân tâm trong sáng." },
    { "观 Guān (Quán)", "☳ ☷ ☷", "Quẻ Quán quan sát từ trên cao, Thiên Địa nhìn rõ, trí tuệ minh bạch." },
    { "噬嗑 Shì Kè (Thệ Hạp)", "☳ ☰ ☳", "Quẻ Thệ Hạp xử lý cấu kết, phá cứng lập mềm, luật lệ bất biến." },
    { "贲 Bì (Bị)", "☷ ☰ ☳", "Quẻ Bị trang hoá vẻ ngoài, nội tâm chuẩn bị cho vận hành lớn." },
    { "剥 Bō (Bác)", "☳ ☷ ☷", "Quẻ Bác bóc tách vỏ ngoài, nội tâm lộ rõ, người biết tự tĩnh." },
    { "复 Fù (Phục)", "☷ ☳ ☷", "Quẻ Phục hồi sau nghịch, trời đất tái hoà, người cần vững chí." },
    { "无妄 Wú Wàng (Vô Vọng)", "☰ ☳ ☵", "Quẻ Vô Vọng thuần tịnh, hành động xuất phát từ chính đạo, không toan tính." },
    { "大畜 Dà Xù (Đại Súc)", "☰ ☳ ☰", "Quẻ Đại Súc tích trữ lớn, như đại dương thu nước, chuẩn bị mạnh mẽ." },
    { "颐 Yí (Dưỡi)", "☳ ☰ ☷", "Quẻ Dưỡi dưỡng thân tâm, ăn ở đúng mực, Thiên Địa dưỡng thành người." },
    { "大过 Dà Guò (Đại Quá)", "☳ ☵ ☳", "Quẻ Đại Quá vượt bậc, bước qua giới hạn, người phải giữ mực để không vỡ." },
    { "坎 Kǎn (Khảm)", "☵ ☳ ☵", "Quẻ Khảm hiểm nguy ngầm, Âm Dương giao nhiễu, cần trí tuệ và can đảm." },
    { "离 Lí (Ly)", "☲ ☵ ☲", "Quẻ Ly lửa sáng rõ, ngọn đuốc dẫn đường, người giữ nhân tâm thanh tịnh." },
    { "咸 Xián (Hãm)", "☵ ☲ ☷", "Quẻ Hãm cảm xúc chạm, Thiên Địa giao cảm, người phải giữ giới trước vận biến." },
    { "恒 Héng (Hằng)", "☷ ☲ ☷", "Quẻ Hằng bền vững, như ngọn núi đứng lâu, người cần kiên định." },
    { "遁 Dùn (Độn)", "☷ ☳ ☵", "Quẻ Độn lui để tiến, Âm hiển Dương ẩn, người biết thời điểm rút lui." },
    { "大壮 Dà Zhuàng (Đại Tráng)", "☳ ☰ ☳", "Quẻ Đại Tráng mạnh mẽ như núi lớn, người phải dùng năng lượng lớn để làm thiện." },
    { "晋 Jìn (Tiến)", "☶ ☰ ☰", "Quẻ Tiến dần lên cao, Thiên Địa đạt độ, người phải giữ nhân đức theo." },
    { "明夷 Míng Yí (Minh Di)", "☲ ☷ ☲", "Quẻ Minh Di ánh sáng bị che, người trí phải giữ tâm sáng giữa bóng tối." },
    { "家人 Jiā Rén (Gia Nhân)", "☳ ☷ ☰", "Quẻ Gia Nhân nội ngoại hoà hợp, tổ ấm thành tựu từ tâm thiện." },
    { "睽 Kuí (Khuê)", "☰ ☲ ☷", "Quẻ Khuê rẽ ngược lối, phá cách nhưng phải có nguyên tắc." },
    { "蹇 Jiǎn (Kiểm)", "☵ ☷ ☵", "Quẻ Kiểm đi qua khó khăn, người giữ yên trong động, khởi hành khi đúng lúc." },
    { "解 Xiè (Giải)", "☵ ☳ ☵", "Quẻ Giải tháo gỡ áp lực, vận hóa xuôi dòng, người cần linh hoạt." },
    { "损 Sǔn (Tổn)", "☳ ☵ ☷", "Quẻ Tổn giảm bớt để tăng trưởng, biết hy sinh nhỏ để đạt lớn." },
    { "益 Yì (Ích)", "☷ ☳ ☰", "Quẻ Ích gia tăng nhân đức, Thiên Địa bênh người thiện." },
    { "夬 Guài (Quải)", "☰ ☳ ☷", "Quẻ Quải quyết đoán, lấy chính Nghĩa là trọng, hành đúng thời." },
    { "姤 Gòu (Cấu)", "☷ ☰ ☵", "Quẻ Cấu gặp duyên bất ngờ, người cần giữ tâm sáng giữa đổi thay." },
    { "萃 Cuì (Tụy)", "☵ ☷ ☳", "Quẻ Tụy hợp nhóm, một người mạnh mẽ kết nối nhiều người thiện." },
    { "升 Shēng (Thăng)", "☳ ☷ ☵", "Quẻ Thăng dâng cao từ nền tảng vững, người cần khiêm trước khi lên." },
    { "困 Kùn (Khốn)", "☵ ☷ ☳", "Quẻ Khốn khó đến, người giữ chí nghị và tĩnh để vượt hoạn." },
    { "井 Jǐng (Tỉnh)", "☷ ☳ ☵", "Quẻ Tỉnh giếng nguồn sống, người phải quay lại nội tâm để tìm lực." },
    { "革 Gé (Cách)", "☳ ☲ ☳", "Quẻ Cách biến đổi lớn, người dám phá cấu cũ để tạo mới." },
    { "鼎 Dǐng (Đỉnh)", "☲ ☳ ☲", "Quẻ Đỉnh vượt thách thức, người nắm quyền tự chủ và trí tuệ." },
    { "震 Zhèn (Chấn)", "☳ ☰ ☳", "Quẻ Chấn rung chuyển mạnh, Thiên Địa dậy phong, người giữ an tâm trong bão." },
    { "艮 Gèn (Cấn)", "☷ ☳ ☷", "Quẻ Cấn núi đứng im, người giữ mình tĩnh để thu thúc nội lực." },
    { "渐 Jiàn (Tiệm)", "☷ ☳ ☰", "Quẻ Tiệm tiến từng bước, không vội mà thành công vững." },
    { "归妹 Guī Mèi (Quy Muội)", "☳ ☲ ☷", "Quẻ Quy Muội bước vào mối liên kết mới, người cần giữ đạo lương." },
    { "丰 Fēng (Phóng)", "☲ ☰ ☲", "Quẻ Phóng phong phú nhân nghĩa, người lan tỏa giá trị tốt đẹp." },
    { "旅 Lǚ (Lữ)", "☵ ☰ ☳", "Quẻ Lữ xa xôi hành trình, người giữ bản năng mạnh mẽ nhưng có định hướng." },
    { "巽 Xùn (Tốn)", "☷ ☲ ☲", "Quẻ Tốn gió nhẹ lan tỏa, người khéo léo uyển chuyển như gió." },
    { "兑 Duì (Đoài)", "☲ ☲ ☷", "Quẻ Đoài hồ nước tĩnh, người vui trong sự chính trực và đàm đạo." },
    { "涣 Huàn (Hoán)", "☵ ☲ ☷", "Quẻ Hoán thay đổi dòng chảy, người cần thích nghi để vươn lên." },
    { "节 Jié (Tiết)", "☷ ☵ ☲", "Quẻ Tiết giữ phép tắc trong biến hóa, người không phá giới mà chuyển hóa." },
    { "中孚 Zhōng Fú (Trung Phù)", "☲ ☵ ☷", "Quẻ Trung Phù tín nghĩa lòng người, Thiên Địa ủng hộ người tin cậy." },
    { "小过 Xiǎo Guò (Tiểu Quá)", "☳ ☲ ☵", "Quẻ Tiểu Quá vượt nhẹ mức, người thong thả khi đã vượt qua bậc đầu." },
    { "既济 Jì Jì (Ký Tế)", "☲ ☵ ☲", "Quẻ Ký Tế hoàn tất chu trình, người có hành động sáng suốt và khiêm nhường." },
    { "未濟 Wèi Jì (Vị Tế)", "☵ ☲ ☵", "Quẻ Vị Tế tới gần hoàn thành nhưng chưa tròn, cần chuẩn bị chín muồi trước bước tiếp." }};

int chonNgauNhien(int n) {
    return std::rand() % n;}

void doiMauConsole() {
#ifdef _WIN32
    HANDLE h = GetStdHandle(STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h, FOREGROUND_GREEN | FOREGROUND_INTENSITY);
#else
    std::cout << "\033[1;32m";
#endif}

void resetMauConsole() {
#ifdef _WIN32
    HANDLE h = GetStdHandle(STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h, FOREGROUND_RED | FOREGROUND_GREEN | FOREGROUND_BLUE);
#else
    std::cout << "\033[0m";
#endif }

void hienThiQue(const Que& q) {
    std::cout << "──────────────────────────────────────────\n";
    std::cout << "Quẻ: " << q.ten << "\n";
    std::cout << "Biểu quẻ: " << q.bieuHao << "\n";
    std::cout << "Giải nghĩa: " << q.loiGiai << "\n";
    std::cout << "──────────────────────────────────────────\n";}

int main() {
    std::srand(static_cast<unsigned int>(std::time(nullptr)));
    doiMauConsole();
    std::cout << "\n   *** VÒNG XOAY KINH DỊCH – THIÊN ĐỊA NHÂN ***\n";
    std::cout << " Nhấn phím Enter để xoay và chọn ngẫu nhiên một quẻ...\n";
    std::cout << "(Gõ 'q' rồi Enter để thoát)\n\n";
    while (true) {
        std::cout << "-> ";
        std::string s;
        std::getline(std::cin, s);
        if (s == "q" || s == "Q") {
            break;}
        int idx = chonNgauNhien(static_cast<int>(dsQue.size()));
        const Que& q = dsQue[idx];
        hienThiQue(q);
        std::cout << "Nhấn Enter để xoay tiếp hoặc 'q' rồi Enter để thoát.\n";}
    resetMauConsole();
    std::cout << "Cảm ơn bạn đã sử dụng Vòng Xoay Kinh Dịch. Hẹn gặp lại!\n";
    return 0;}
```0
