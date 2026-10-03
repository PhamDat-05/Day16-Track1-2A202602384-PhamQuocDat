# Memo Teardown – NotebookLM (nay là Gemini Notebook)

**Họ tên:** Phạm Quốc Đạt  
**Bài:** Day 16 – Track 1 – AI Product Manager  
**Ngày phân tích:** 03/10/2026  
**Phạm vi dự đoán:** 04–10/2027 (6–12 tháng tới).

**Vì sao chọn sản phẩm này:** NotebookLM giải quyết một việc cụ thể: biến tập tài liệu thành hiểu biết và đầu ra có thể sử dụng. Sản phẩm có lịch sử công khai đủ dài để phân tích sự chuyển dịch từ trợ lý đọc tài liệu sang môi trường nghiên cứu và làm việc dựa trên nguồn.

**Luận điểm chính:** Lợi thế của sản phẩm nằm ở chuỗi công việc “chọn nguồn → hiểu → kiểm chứng → tạo đầu ra”, thay vì chỉ ở khả năng trả lời của model. Khi mở rộng sang tìm nguồn, chạy mã và kết nối hệ sinh thái Google, giá trị tăng lên nhưng yêu cầu kiểm soát nguồn và độ tin cậy cũng cao hơn.

**Cách đọc:** Sự kiện dựa trên nguồn công khai; nguyên lý, JTBD và dự đoán là suy luận. Không có khảo sát hoặc thử nghiệm trực tiếp; tệp hiện tại không đại diện tỷ trọng toàn bộ người dùng.

## §1. Timeline các cập nhật lớn

| Thời điểm | Cập nhật | Context lúc đó | Revert về nguyên lý |
|---|---|---|---|
| **M1 · 12/07/2023** | Project Tailwind bắt đầu triển khai với tên NotebookLM cho nhóm nhỏ tại Mỹ; trợ lý tóm tắt, giải thích và kết nối ý tưởng từ nguồn người dùng chọn. [S1] | Google mô tả vấn đề từ trao đổi với sinh viên, giảng viên và người làm việc tri thức: có nhiều tài liệu nhưng mất thời gian tổng hợp và nối các ý. | **Định nghĩa “tốt” theo JTBD:** Với nghiên cứu, câu trả lời tốt phải liên quan đến tài liệu đang làm việc. Giới hạn vào nguồn chọn giúp tối ưu một công việc rõ ràng thay vì cạnh tranh bằng độ rộng của chatbot. |
| **M2 · 06/06/2024** | Mở rộng tới hơn 200 quốc gia/vùng lãnh thổ; dùng Gemini 1.5 Pro, thêm Slides và URL, trích dẫn dẫn tới đoạn nguồn. [S2] | Model đa phương thức tạo điều kiện xử lý hình, biểu đồ. Google ghi nhận tác giả, sinh viên và nhà giáo đã đưa sản phẩm vào nghiên cứu, viết lách. | **Wrapper/moat từ workflow:** Model tốt hơn là nền tảng; tổ chức nguồn và truy vết bằng chứng tạo giá trị sử dụng. Giảm công đổi định dạng và kiểm chứng giúp sản phẩm đi sâu vào quy trình, nhưng chưa chứng minh một moat bền vững. |
| **M3 · 11/09/2024** | Audio Overviews chuyển tài liệu thành cuộc trao đổi giữa hai người dẫn AI, có thể tải xuống để nghe. [S3] | Sản phẩm đã mở rộng toàn cầu nhưng trải nghiệm chủ yếu vẫn là đọc và hỏi đáp. Bản đầu chỉ có tiếng Anh, có thể sai và chưa cho ngắt lời. | **x10 qua thay đổi trải nghiệm:** Mở thời gian sử dụng khi người dùng không tiện đọc; giảm công tự biến tài liệu thành nội dung nghe. Đây là giả thuyết về bước nhảy giá trị, không phải bằng chứng năng suất đã tăng đúng 10 lần. |
| **M4 · 13/12/2024** | Ra NotebookLM Plus cho người dùng chuyên sâu, đội nhóm và tổ chức; tăng giới hạn, có notebook nhóm và analytics; đồng thời thêm tương tác Audio và giao diện Sources–Chat–Studio. [S4] | Sau Audio, Google công bố mức sử dụng đáng kể. Sản phẩm cần phục vụ cả học cá nhân lẫn công việc tập thể, với quản lý nguồn và đầu ra trong cùng trải nghiệm. | **Wrapper/moat và phân tầng theo giá trị:** Khả năng chia sẻ, quản lý và bảo vệ dữ liệu đưa AI vào workflow tổ chức; gói trả phí gắn với cường độ sử dụng và phối hợp, thay vì chỉ bán một câu trả lời tốt hơn. |
| **M5 · 13/11/2025** | Deep Research lập kế hoạch, tìm kiếm và tạo báo cáo; báo cáo cùng nguồn có thể nhập lại notebook. Thêm Sheets, ảnh và Word vào nhóm nguồn hỗ trợ. [S5] | Người dùng trước đó phải tự chuẩn bị tập nguồn; tài liệu thực tế lại nằm ở nhiều định dạng. Việc tìm và tập hợp bằng chứng trở thành một nút thắt đầu vào. | **x10 bằng xử lý nút thắt:** Tự động hóa một phần thu thập nguồn mở rộng giá trị từ “hiểu tài liệu đã có” sang “bắt đầu nghiên cứu”. Người dùng vẫn cần duyệt nguồn, vì tăng số nguồn không đồng nghĩa tăng chất lượng. |
| **M6 · 08/06/2026** | Nâng cấp nghiên cứu với máy tính đám mây chạy mã; thêm đầu ra như báo cáo, biểu đồ, bảng tính và slide có thể tải xuống. Trang nguồn được cập nhật ngày 16/07/2026. [S6] | Công việc của analyst và program manager không kết thúc ở một đoạn tóm tắt: họ còn cần phân tích và bàn giao đầu ra. Triển khai ban đầu nhắm các gói Ultra và Workspace được chỉ định. | **Định nghĩa “tốt” theo đầu ra công việc:** Giá trị chuyển sang hoàn thành một phần dự án có thể bàn giao. Chạy mã có thể hỗ trợ tính toán nhưng không tự bảo đảm dữ liệu, giả định và kết luận đúng. |
| **M7 · 16/07/2026** | Đổi tên thành Gemini Notebook; giữ sản phẩm độc lập, kết nối notebook với ứng dụng Gemini; công bố hướng đưa notebook vào AI Mode của Search. [S7] | Google muốn bộ nguồn theo người dùng giữa các nơi họ làm việc. Đây là mở rộng phân phối và tính liên tục của ngữ cảnh, không chỉ đổi thương hiệu. | **Moat từ workflow và hệ sinh thái:** Tái sử dụng cùng bộ nguồn qua nhiều điểm truy cập làm giảm công khởi tạo lại. Lợi thế giữ chân có thể đến từ thói quen và ngữ cảnh dự án; không nên đánh đồng điều đó với dữ liệu không thể xuất. |

**Vì sao chọn những mốc này?** Bảy mốc thay đổi lần lượt cách định nghĩa giá trị, phạm vi tiếp cận, hình thức tiêu thụ, đối tượng trả tiền, đầu vào nghiên cứu, đầu ra công việc và phân phối. Tôi loại mốc 26/09/2024 bổ sung YouTube/audio khỏi bảng chính vì, dù hữu ích, nó chủ yếu mở thêm định dạng nguồn; M5 thể hiện sự thay đổi sâu hơn ở công đoạn thu thập bằng chứng. [S8] M7 được giữ vì gắn với kết nối ngữ cảnh giữa sản phẩm, không phải vì tên mới.

**Phân biệt nguyên lý:** Phục vụ nhiều lĩnh vực chưa đủ để gọi NotebookLM là Vertical AI. Vòng lặp học ở đây là phản hồi người dùng → điều chỉnh roadmap [S9], không phải dùng tài liệu riêng để huấn luyện model.

## §2. Tệp user & JTBD

| Tiêu chí | Early adopters: người nghiên cứu/viết đã có nguồn | Tệp hiện tại mở rộng: người bàn giao công việc trong tổ chức |
|---|---|---|
| **Đặc điểm cụ thể** | Tác giả phi hư cấu, sinh viên làm khóa luận hoặc giảng viên có tập bài báo, ghi chú và bản phỏng vấn; chấp nhận thử sản phẩm mới để giảm công tổng hợp. Google ghi nhận các nhóm này và trường hợp Walter Isaacson nghiên cứu nhật ký Marie Curie. [S1–S2] | Analyst tổng hợp dữ liệu nhiều nơi để làm báo cáo; program manager chuyển tài liệu kỹ thuật thành hướng dẫn và kế hoạch cho đội nhóm. Đây là workflow Google nêu năm 2026, chưa phải bằng chứng tỷ lệ sử dụng thực tế. [S6] |
| **JTBD chính** | Khi có nhiều tài liệu về một chủ đề, tôi muốn nối các luận điểm với bằng chứng gốc để viết hoặc học mà không bỏ sót thông tin quan trọng. | Khi phải bàn giao kết quả từ tài liệu và dữ liệu rời rạc, tôi muốn tạo bản phân tích và tài liệu làm việc có thể kiểm tra, để đội nhóm ra quyết định và thực hiện bước tiếp theo. |
| **Trước đó làm bằng cách nào?** | Đọc, đánh dấu PDF, ghi chú trong Docs/Word, tự lập dàn ý và tra lại từng nguồn. Đây là phương án thay thế suy luận từ công việc, không phải kết quả phỏng vấn. | Tìm tài liệu trên Drive/web, tổng hợp thủ công, xử lý số liệu trong bảng tính và soạn slide/báo cáo ở công cụ riêng. Đây cũng là suy luận về workflow thay thế. |
| **Định nghĩa kết quả tốt** | Hiểu đúng ý tác giả, tìm lại được đoạn bằng chứng và tạo được bản nháp phục vụ bài viết/bài học. | Số liệu và giả định có thể kiểm tra, đầu ra sửa được và đồng nghiệp tiếp tục sử dụng được. |

**Dịch chuyển tệp:** M4 tạo điều kiện cho đội nhóm dùng chung và trả tiền; M5 giảm yêu cầu phải có sẵn nguồn; M6 hỗ trợ đầu ra có thể bàn giao. Các bước này mở rộng JTBD từ đọc/viết cá nhân sang nghiên cứu phục vụ công việc. Tuy nhiên, giáo dục vẫn là tệp được đầu tư: flashcards, quizzes và Learning Guide đã xuất hiện năm 2025 [S10]; đây là mở rộng tệp, chưa có căn cứ kết luận sản phẩm bỏ sinh viên.

### Switching cost theo 4 forces

Phân tích dưới đây xét việc một analyst đang tổng hợp tài liệu bằng Drive, bảng tính và chatbot riêng **chuyển sang Gemini Notebook rồi duy trì sử dụng**.

| Lực | Cơ chế trong tình huống này | Tác động tới chuyển đổi/ở lại |
|---|---|---|
| **Push – vấn đề với cách cũ** | Mất công chuyển giữa tài liệu, hỏi đáp, tính toán và soạn báo cáo; khó giữ quan hệ giữa kết luận và nguồn. | Tạo động lực thử sản phẩm. Nếu quy trình cũ đã nhanh và ổn định, lực này yếu đi. |
| **Pull – sức hút giải pháp mới** | Bộ nguồn theo dự án, hỏi đáp có trích dẫn, tìm nguồn và tạo đầu ra trong một luồng; M2, M5–M6 là tín hiệu chức năng. | Hút người dùng vào; sau khi áp dụng, khả năng tái sử dụng notebook tạo lý do tiếp tục dùng. |
| **Habit – thói quen hiện tại** | Lúc mới chuyển: quen Docs/Excel và tự kiểm chứng. Sau khi chuyển: quen lưu nguồn theo notebook và trao đổi cùng đội nhóm ở đó. | Ban đầu cản gia nhập; về sau giữ người dùng ở lại. Công chọn lại nguồn và dựng lại ngữ cảnh là chi phí thực tế, dù file gốc vẫn còn bên ngoài. |
| **Anxiety – lo ngại giải pháp mới** | Sợ báo cáo sai, trích dẫn không hỗ trợ kết luận, dữ liệu nhạy cảm hoặc giới hạn gói không phù hợp. | Cản chuyển đổi. Khi cân nhắc rời đi, lo công cụ thay thế không giữ được workflow kiểm chứng có thể giữ người dùng lại. Cần kiểm tra chính sách và chất lượng thực tế trước khi áp dụng. |

**Lực giữ chân mạnh nhất – phán đoán:** Với đội nhóm đã có nhiều notebook, Habit có thể mạnh nhất vì ngữ cảnh đã được tuyển chọn và cách phối hợp đã thành nếp. Nếu công cụ khác nhập được đầy đủ nguồn, ghi chú và mối liên hệ bằng chứng với ít công sức, lực này giảm; đội nhóm sẽ so sánh chất lượng và tổng chi phí thay vì ở lại vì công dựng lại dự án. Với người chỉ tạo một Audio Overview rồi tải xuống, switching cost thấp hơn nhiều.

## §3. Ba dự đoán hướng đi (6–12 tháng tới)

### Dự đoán 1 – Mở rộng tính năng: kiểm tra và tái tạo phân tích

- **Dự đoán:** Gemini Notebook sẽ tăng khả năng xem lại hoặc chạy lại các bước phân tích số liệu, qua việc làm rõ dữ liệu nguồn, phép tính hoặc giả định trong đầu ra. **Độ tin cậy: trung bình.**
- **Lập luận:** M6 đưa sản phẩm vào công việc tạo bảng tính và báo cáo; tệp analyst ở §2 cần kiểm tra kết quả trước bàn giao. Chỉ tạo được file chưa hoàn thành JTBD này. Tín hiệu xác nhận là tính năng truy vết phép tính hoặc tái chạy phân tích được công bố; dự đoán suy yếu nếu đầu tư chủ yếu vào trình bày và lượng định dạng xuất.

### Dự đoán 2 – Mở rộng segment: mẫu workflow cho nhóm công việc

- **Dự đoán:** Sản phẩm sẽ cung cấp thêm mẫu notebook/đầu ra cho onboarding, nghiên cứu thị trường hoặc tổng hợp tài liệu kỹ thuật, giúp đội nhóm bắt đầu từ công việc cụ thể. **Độ tin cậy: trung bình–khá.**
- **Lập luận:** M4 xây lớp đội nhóm, M5 giảm công tìm nguồn và M6 mở khả năng bàn giao. §2 cho thấy người làm việc tri thức cần lặp lại một quy trình, không chỉ hỏi một câu. Tín hiệu xác nhận là mẫu theo workflow hoặc hướng dẫn triển khai cho tổ chức. Đây là dự đoán về đóng gói trải nghiệm, chưa phải dự đoán Google xây Vertical AI chuyên ngành có moat chuyên môn.

### Dự đoán 3 – Mô hình kiếm tiền: phân tầng theo khối lượng công việc

- **Dự đoán:** Google sẽ tiếp tục dùng giới hạn tác vụ nghiên cứu, phân tích và tạo đầu ra để phân biệt gói cá nhân với các gói trả phí cao hơn/Workspace. **Độ tin cậy: khá; không dự đoán mức giá cụ thể.**
- **Lập luận:** M4 đã phân tầng bằng giới hạn sử dụng và giá trị đội nhóm; M6 triển khai năng lực nâng cao trước cho nhóm gói được chỉ định. Với người dùng tổ chức ở §2, giá trị nằm ở công việc hoàn thành và thời gian tiết kiệm. Tín hiệu xác nhận là bảng quyền lợi phân biệt quota của tác vụ nâng cao; dự đoán suy yếu nếu các gói được san bằng giới hạn đáng kể.

**Dự đoán tự tin nhất:** Dự đoán 3 vì nối trực tiếp hai quyết định kiếm tiền/triển khai đã quan sát. Giả định có thể làm nó sai là Google ưu tiên trợ cấp rộng để tăng phân phối và kiếm tiền ở phần khác của hệ sinh thái. Kết nối với Search đã được công bố tại M7, nên không được trình bày như một ý tưởng tương lai mới do memo dự đoán.

## §4. AI Log

AI được dùng nhiều trong bài này, gồm cả nghiên cứu và đề xuất lập luận. Không ghi nhận người học đã tự mở nguồn, tự thử sản phẩm hoặc tự đưa ra các phán đoán dưới đây khi chưa có bằng chứng rằng các việc đó đã diễn ra.

| Việc | AI làm hay bạn làm? | Kiểm chứng/phán đoán lại như thế nào? |
|---|---|---|
| Xác định yêu cầu và cấu trúc | Người học cung cấp đề/CP và yêu cầu hoàn thiện; AI đọc 13 ảnh, rút cấu trúc. | AI đối chiếu yêu cầu CP0–CP4: 6–8 mốc, 4 phần, 3 dự đoán, AI Log và file `memo.md`. |
| Chọn sản phẩm, tìm và kiểm tra timeline | AI đề xuất NotebookLM, tìm nguồn công khai và mở bài Google gốc. | AI kiểm tra ngày và nội dung trong từng nguồn, phát hiện tên mới năm 2026; phân biệt ngày đăng M6 với ngày cập nhật trang. Người học chưa được ghi nhận đã tự kiểm chứng. |
| Chọn 7 mốc và revert nguyên lý | AI đề xuất lựa chọn và lập luận. | AI dùng tiêu chí thay đổi JTBD, segment, kiếm tiền hoặc workflow; loại một mốc bổ sung định dạng. Đây là suy luận AI, cần người học đọc và quyết định có đồng ý trước nộp. |
| Tệp user, JTBD và 4 forces | AI tổng hợp ví dụ công khai, xây tình huống và phán đoán. | Phân biệt early adopters được Google ghi nhận với workflow mục tiêu; không suy ra tỷ trọng người dùng. Không có phỏng vấn, khảo sát hay thử nghiệm cá nhân. |
| Ba dự đoán | AI đề xuất; chưa có phán đoán độc lập của người học được ghi nhận. | Mỗi dự đoán nối về M1–M7/§2, có độ tin cậy và tín hiệu làm suy yếu; không coi hướng đã công bố là dự đoán mới. |
| Biên tập file nộp | AI soạn Markdown và kiểm tra cấu trúc. | AI kiểm tra số mốc, số dự đoán, nguồn và bảng AI Log. Người học cần xác nhận họ tên và đọc lại các nhận định để chịu trách nhiệm cho bài nộp. |

**Phần AI làm nhiều nhất:** Revert nguyên lý và dự đoán. Chuỗi lập luận là: tổ chức nguồn → hiểu và kiểm chứng → hoàn thành công việc → tạo giá trị trả phí cho đội nhóm. Người học cần tự giải thích và quyết định có đồng ý với chuỗi này trước nộp.

### Nguồn công khai

Các nguồn dưới đây được AI mở và đối chiếu ngày 03/10/2026. Nguồn Google giúp xác nhận công bố, nhưng không thay thế đánh giá độc lập về hiệu quả sản phẩm.

- **[S1]** Google, 12/07/2023: [Introducing NotebookLM](https://blog.google/innovation-and-ai/technology/ai/notebooklm-google-ai/).
- **[S2]** Google, 06/06/2024: [NotebookLM goes global with Slides support and better ways to fact-check](https://blog.google/innovation-and-ai/products/notebooklm-goes-global-support-for-websites-slides-fact-check/).
- **[S3]** Google, 11/09/2024: [NotebookLM now lets you listen to a conversation about your sources](https://blog.google/innovation-and-ai/products/notebooklm-audio-overviews/).
- **[S4]** Google, 13/12/2024: [NotebookLM gets a new look, audio interactivity and a premium version](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-new-features-december-2024/).
- **[S5]** Google, 13/11/2025: [NotebookLM adds Deep Research and support for more source types](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-deep-research-file-types/).
- **[S6]** Google, đăng 08/06/2026, cập nhật 16/07/2026: [Do better research with NotebookLM](https://blog.google/innovation-and-ai/products/notebooklm/better-research-notebooklm/). Memo sử dụng nội dung hiện có trên trang đã cập nhật; không khẳng định từng chi tiết đều có trong bản đăng đầu tiên.
- **[S7]** Google, 16/07/2026: [NotebookLM is now Gemini Notebook](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/?hl=fi).
- **[S8]** Google, 26/09/2024: [NotebookLM adds audio and YouTube support](https://blog.google/innovation-and-ai/products/notebooklm-audio-video-sources/).
- **[S9]** Google, 29/07/2025: [The inside story of building NotebookLM](https://blog.google/innovation-and-ai/products/developing-notebooklm/).
- **[S10]** Google: [6 ways to use NotebookLM to master any subject](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-student-features/).
