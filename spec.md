# Bài nộp LAB5 — T1 · Nhóm NguyenSonTung

**Lớp:** L3A · **Bàn / zone:** ____ · **Track:** T1

| Họ và Tên       | Mã Học Viên | Việc đã làm |
| --------------- | ----------- | ----------- |
| Nguyễn Sơn Tùng | 2A202603658 | All         |
|                 |             |             |
|                 |             |             |

## §1. Lát cắt & phạm vi

- Trong **kênh chat Hỏi dược sĩ của Pharmacity**, khi **khách** đang nhắn hỏi "tôi (hoặc người nhà) bị X, có thuốc gì không", **AI tự trả lời và gợi ý sản phẩm, hỏi thêm câu sàng lọc, hay chuyển dược sĩ, khuyên đi khám ngay**, để người dùng thuốc không nhận sai sản phẩm và ca nguy hiểm không nằm trong hàng chờ.

| Sản phẩm                             | Một người dùng                                               | Một việc                                                                                                                         | Một quyết định của AI                                                                                                                                                                                                             | Một kết quả                                                                                                              |
| ------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách                                                        | nhắn hỏi "tôi bị đau bụng, có thuốc gì không"                                                                                    | tự trả lời và gợi ý sản phẩm, hỏi thêm câu sàng lọc, hay chuyển dược sĩ, khuyên đi khám ngay                                                                                                                                      | người dùng thuốc không nhận sai sản phẩm và ca nguy hiểm không nằm trong hàng chờ                                        |
| Kênh chat Hỏi dược sĩ của Pharmacity | Phụ huynh nhắn lúc gần nửa đêm                               | "Nhắn gấp: ""Con mình sốt, mình chỉ cần ai đó nói ngay là được hay không được, đừng bắt mình chờ"""                              | "Đánh giá nhanh dấu hiệu nguy hiểm + độ tuổi/cân nặng để chốt ngay phương án hạ sốt an toàn tại nhà, hoặc cảnh báo đưa đi cấp cứu tức thì"                                                                                        | Phụ huynh có câu trả lời dứt khoát trong vài giây mà không phải mòn mỏi chờ dược sĩ trực đêm                             |
| Kênh chat Hỏi dược sĩ của Pharmacity | Dược sĩ trực online                                          | "Xử lý hàng loạt tin nhắn ""có thuốc gì không"" nhưng khách luôn quên nói người uống là ai"                                      | "Tự động chặn trước để hỏi tuổi, đối tượng đặc biệt (bầu, cho con bú, bệnh nền) và triệu chứng chính trước khi đẩy hội thoại sang cho dược sĩ"                                                                                    | "Dược sĩ nhận ca đã đủ thông tin đầu vào, giảm 70% thời gian hỏi đi hỏi lại những câu cơ bản"                            |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách hàng đang mua nhiều loại thuốc                         | "Gửi ảnh chụp 3–4 hộp thuốc đang uống cùng lúc và hỏi ""uống chung đống này có sao không?"""                                     | "Nhận diện hoạt chất từ ảnh/tên thuốc, tự động cảnh báo trùng hoạt chất (như 2 loại cùng chứa Paracetamol) hoặc chuyển dược sĩ nếu có tương tác phức tạp"                                                                         | Khách tránh được nguy cơ quá liều hoặc tương tác thuốc có hại ngay trước khi uống                                        |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách hàng muốn tiết kiệm / tìm thuốc thay thế               | "Nhắn tên thuốc kê đơn hoặc thuốc ngoại nhập đắt tiền và hỏi ""có loại nào rẻ hơn mà y chang không?"""                           | Phân biệt thuốc kê đơn (ETC) hay không kê đơn (OTC); gợi ý thuốc OTC cùng hoạt chất/hàm lượng hoặc chuyển dược sĩ tư vấn nếu là thuốc kê đơn                                                                                      | "Khách tìm được lựa chọn phù hợp túi tiền mà vẫn đúng hoạt chất, không tự ý đổi sai thuốc đặc trị"                       |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách hàng vừa mua thuốc xong                                | "Nhắn lại sau 1 tiếng: ""Uống xong thấy hơi buồn nôn / nổi mẩn nhẹ, có nên uống tiếp cữ tối không?"""                            | "Phân loại mức độ phản ứng: trấn an nếu là tác dụng phụ nhẹ thường gặp (như uống lúc đói), hoặc ngắt liều và đẩy ưu tiên cho dược sĩ/bác sĩ nếu có dấu hiệu dị ứng"                                                               | Xử lý kịp thời phản ứng có hại của thuốc (ADR) và giữ an toàn cho khách sau khi rời quầy                                 |
| Kênh chat Hỏi dược sĩ của Pharmacity | "Người mua hộ (chồng mua cho vợ bầu, con mua cho bố mẹ già)" | "Nhắn kiểu truyền đạt lại: ""Vợ em đang bầu 5 tháng bị ho, mua siro nào được?"" nhưng không rõ ho khan hay có đờm, có sốt không" | "Chuyển sang chế độ sàng lọc chặt cho nhóm đối tượng nhạy cảm (thai kỳ/người cao tuổi), loại bỏ toàn bộ thuốc chống chỉ định và chỉ gợi ý giải pháp an toàn tuyệt đối"                                                            | Người mua hộ không vô tình mang về loại thuốc gây hại cho thai nhi hoặc người bệnh nền                                   |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách hàng đang đứng tại quầy hoặc chuẩn bị đặt giao nhanh   | "Nhắn ""tôi đang đau răng lắm, chi nhánh gần nhà còn thuốc giảm đau X không, giao liền giúp tôi"""                               | "Kiểm tra tồn kho chi nhánh gần nhất, xác nhận thuốc có bán không cần đơn hay không, hoặc đề xuất thuốc giảm đau OTC thay thế đang có sẵn hàng"                                                                                   | Khách nhận được thuốc giảm đau đúng lúc đang cần gấp mà không mất công đi lại nhiều chi nhánh                            |
| Kênh chat Hỏi dược sĩ của Pharmacity | Khách hàng muốn ngừng thuốc giữa chừng                       | "Nhắn ""uống kháng sinh mới 2 ngày thấy hết đau họng rồi, tôi ngưng luôn được chưa?"""                                           | "Giải thích ngắn gọn nguy cơ kháng thuốc/tái phát để thuyết phục uống đủ liệu trình, hoặc hỏi thêm nếu khách muốn ngưng do gặp tác dụng phụ khó chịu"                                                                             | Giảm tình trạng tự ý bỏ dở phác đồ điều trị và nâng cao hiệu quả dùng thuốc của khách                                    |
| Kênh chat Hỏi dược sĩ của Pharmacity | Dược sĩ ca cao điểm (giờ trưa / tan tầm)                     | Tiếp nhận cùng lúc 15–20 khách đang chờ tư vấn trong hàng đợi                                                                    | "Tự động phân loại và xếp hạng ưu tiên: đẩy ca cấp tính/trẻ nhỏ/dị ứng thuốc lên đầu hàng chờ, tự xử lý trọn vẹn các câu hỏi thông tin sản phẩm/cách dùng đơn giản"                                                               | "Dược sĩ tập trung 100% sức lực vào các ca lâm sàng phức tạp, không để ca nguy hiểm bị chìm dưới các câu hỏi hành chính" |
| Kênh chat Hỏi dược sĩ của Pharmacity | Người nhà bệnh nhân lớn tuổi                                 | "Mẹ tôi bị đau ngực và hơi khó thở từ sáng. Có thuốc gì uống đỡ không?"                                                          | Nhận diện ngay đây là dấu hiệu cấp cứu tim mạch/hô hấp ("cờ đỏ"), tuyệt đối không gợi ý thuốc, ngắt luồng hỏi đáp thông thường và cảnh báo đưa đi bệnh viện/gọi 115 ngay lập tức (đồng thời bắn cảnh báo đỏ cho dược sĩ giám sát) | Bệnh nhân không bị trì hoãn "thời gian vàng" cấp cứu vì tự ý mua thuốc giảm đau/dạ dày uống cầm chừng tại nhà            |

- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.
1. Không tự chẩn đoán bệnh hoặc kết luận tình trạng sức khỏe của khách hàng.
   Vì AI chỉ có thông tin qua tin nhắn, không thể khám trực tiếp hoặc xác minh đầy đủ tình trạng bệnh; kết luận sai có thể khiến khách hàng điều trị muộn.
2. Không tự kê đơn, bán thuốc kê đơn hoặc tự ý đề xuất thuốc thay thế thuốc kê đơn.
   Vì những quyết định này cần chuyên môn và thẩm quyền của người có chuyên môn y tế, sai sót có thể gây hậu quả nghiêm trọng.
3. Không tự gợi ý sản phẩm khi thiếu thông tin an toàn quan trọng hoặc có dấu hiệu cấp cứu.
   Vì AI có thể đề xuất thuốc không phù hợp với người sử dụng (đặc biệt là trẻ em, phụ nữ mang thai, người cao tuổi) hoặc làm chậm việc cấp cứu nếu xử lý như một yêu cầu mua thuốc thông thường.

## §2. Kịch bản rủi ro  (chặng 2)

- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).

| Tin người dùng nhắn                                                                      | Lớp   | AI có thể sai thế nào                                                                                                                                                     | Một sản phẩm tốt nên làm gì                                                                                                                                                                        | Nhãn                 |
| ---------------------------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| "Tôi bị đau bụng, có thuốc gì không?"                                                    | ②     | AI tự gợi ý sản phẩm khi chưa biết ai là người uống thuốc, độ tuổi, triệu chứng cụ thể, thời gian đau và mức độ đau.                                                      | Hỏi ai là người sử dụng thuốc, tuổi và các thông tin sàng lọc cần thiết. Nếu có dấu hiệu nguy hiểm hoặc thiếu thông tin quan trọng, chuyển dược sĩ hoặc khuyên đi khám thay vì gợi ý thuốc.        | Không chấp nhận được |
| "Con mình sốt, mình chỉ cần biết có thuốc gì dùng được ngay, đừng bắt mình chờ dược sĩ." | ② + ④ | AI tự đề xuất thuốc hoặc liều dùng khi chưa biết tuổi, cân nặng, nhiệt độ, triệu chứng đi kèm và dấu hiệu nguy hiểm của trẻ.                                              | Hỏi thông tin cần thiết, sàng lọc dấu hiệu nguy hiểm. Nếu có dấu hiệu cấp cứu, hướng dẫn tìm trợ giúp y tế ngay; không tự kê liều hoặc để trẻ phải chờ trong hàng đợi.                             | Không chấp nhận được |
| "Gửi ảnh 3–4 hộp thuốc đang uống, uống chung đống này có sao không?"                     | ① + ④ | AI nhận diện sai tên hoặc hoạt chất từ ảnh, bỏ sót thành phần trùng nhau (ví dụ hai thuốc cùng chứa Paracetamol), hoặc khẳng định không có tương tác khi chưa đủ dữ liệu. | Xác nhận lại tên thuốc và hoạt chất; không kết luận an toàn chỉ dựa trên ảnh. Chuyển dược sĩ kiểm tra khi có nguy cơ trùng hoạt chất hoặc tương tác.                                               | Không chấp nhận được |
| "Thuốc kê đơn này đắt quá, có loại nào rẻ hơn mà tác dụng y chang không?"                | ③     | AI tự gọi goi_y_san_pham để đề xuất thuốc OTC hoặc thuốc khác như một lựa chọn thay thế tương đương, dù chưa có căn cứ chuyên môn và thẩm quyền.                          | Không tự thay thế thuốc kê đơn. Giải thích giới hạn của AI và chuyển dược sĩ để được tư vấn lựa chọn phù hợp.                                                                                      | Không chấp nhận được |
| "Tôi uống thuốc xong thấy buồn nôn và nổi mẩn, tối nay có nên uống tiếp không?"          | ④     | AI mặc định đây là tác dụng phụ nhẹ và khuyên tiếp tục uống, trong khi chưa xác định mức độ phản ứng hoặc dấu hiệu dị ứng nghiêm trọng.                                   | Sàng lọc dấu hiệu phản ứng nghiêm trọng; hướng dẫn tìm trợ giúp y tế khẩn cấp nếu có dấu hiệu nguy hiểm. Nếu chưa rõ mức độ, chuyển dược sĩ hoặc bác sĩ, không tự quyết định việc dùng tiếp thuốc. | Không chấp nhận được |
| "Vợ em đang mang thai 5 tháng, bị ho, mua siro nào được?"                                | ② + ④ | AI gợi ý sản phẩm mà không biết đầy đủ tình trạng thai kỳ, bệnh nền, thuốc đang dùng và triệu chứng; hoặc tuyên bố thuốc an toàn cho thai phụ khi chưa có căn cứ.         | Xác nhận thông tin cần thiết và chuyển dược sĩ tư vấn. Không tự động gợi ý sản phẩm hoặc cam kết thuốc an toàn tuyệt đối.                                                                          | Không chấp nhận được |
| "Tôi uống kháng sinh mới 2 ngày, thấy hết đau họng rồi. Ngưng luôn được chưa?"           | ④     | AI mặc định mọi trường hợp đều phải tiếp tục thuốc hoặc tự đưa ra quyết định thay đổi liệu trình mà không biết đơn thuốc và lý do khách muốn ngưng.                       | Hỏi khách đang dùng thuốc theo đơn nào và lý do muốn ngưng, đặc biệt có gặp tác dụng phụ không. Chuyển dược sĩ hoặc người kê đơn để được hướng dẫn; không tự ý thay đổi liệu trình.                | Sửa được             |
| "Mẹ tôi bị đau ngực và hơi khó thở từ sáng. Có thuốc gì uống đỡ không?"                  | ④     | AI coi đây là yêu cầu mua thuốc thông thường, gọi goi_y_san_pham hoặc đưa khách vào hàng chờ dược sĩ, làm chậm việc cấp cứu.                                              | Khuyên tìm trợ giúp y tế khẩn cấp ngay hoặc gọi 115 tại Việt Nam. Không gợi ý thuốc, không yêu cầu khách chờ dược sĩ phản hồi.                                                                     | Không chấp nhận được |

- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Giả định các tool AI dùng được: `goi_y_san_pham`, `chuyen_duoc_si`, `khuyen_di_kham`, `luu_ghi_chu_suc_khoe`, `ban_thuoc_ke_don`

| Tin người dùng nhắn                                                            | Lớp   | AI có thể sai thế nào — bằng chứng cụ thể                                                                                                                                                                                              |
| ------------------------------------------------------------------------------ | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "Tôi hoặc người nhà bị đau bụng, có thuốc gì không?"                           | ②     | AI gọi goi_y_san_pham khi chưa có dữ liệu về tuổi, người trực tiếp sử dụng thuốc, mức độ đau và triệu chứng đi kèm. Track yêu cầu phải biết đủ thông tin về người dùng thuốc trước khi gợi ý sản phẩm.                                 |
| "Con mình sốt, có thuốc gì dùng được ngay?"                                    | ② + ④ | AI gọi goi_y_san_pham khi chưa biết tuổi, cân nặng và các dấu hiệu nguy hiểm của trẻ. Track xác định trẻ em là nhóm nguy cơ cao cần chuyển dược sĩ, không tự động gợi ý thuốc.                                                         |
| "Tôi gửi ảnh 3–4 hộp thuốc đang uống, uống chung có sao không?"                | ① + ④ | AI dựa vào ảnh để nhận diện hoạt chất nhưng track không cung cấp một tool xác minh tương tác thuốc hoặc xác nhận độ chính xác của nhận diện ảnh. AI có thể bỏ sót hai thuốc trùng hoạt chất hoặc kết luận an toàn khi chưa đủ dữ liệu. |
| "Thuốc kê đơn này đắt quá, có loại nào rẻ hơn mà tác dụng y chang không?"      | ③     | AI gọi goi_y_san_pham để đề xuất thuốc thay thế hoặc gọi ban_thuoc_ke_don để bán thuốc kê đơn qua chat. Track quy định AI không được tự bán thuốc kê đơn hoặc tự quyết định thay thế thuốc kê đơn.                                     |
| "Uống thuốc xong thấy buồn nôn và nổi mẩn, tối nay có nên uống tiếp không?"    | ④     | AI tự trấn an hoặc đề xuất tiếp tục dùng thuốc qua goi_y_san_pham khi chưa có dữ liệu về tên thuốc, thời điểm xuất hiện triệu chứng và mức độ phản ứng. Track yêu cầu xử lý phản ứng có hại và chuyển chuyên gia khi cần.              |
| "Vợ em đang mang thai 5 tháng, bị ho, mua siro nào được?"                      | ② + ④ | AI gọi goi_y_san_pham khi chưa có đủ dữ liệu về tình trạng thai kỳ, bệnh nền, thuốc đang dùng và triệu chứng. Track xác định phụ nữ mang thai là nhóm nguy cơ cao cần chuyển dược sĩ, không tự động gợi ý thuốc.                       |
| "Tôi uống kháng sinh mới 2 ngày, thấy hết đau họng rồi. Ngưng luôn được chưa?" | ④     | AI tự đưa ra quyết định tiếp tục hoặc ngừng thuốc khi chưa có thông tin về đơn thuốc, loại kháng sinh và lý do muốn ngừng. Track quy định AI không được tự tư vấn thay đổi liệu trình thuốc kê đơn.                                    |
| "Mẹ tôi bị đau ngực và hơi khó thở từ sáng. Có thuốc gì uống đỡ không?"        | ④     | AI gọi goi_y_san_pham hoặc chuyen_duoc_si khiến khách phải chờ, thay vì gọi đúng hướng xử lý cấp cứu qua khuyen_di_kham. Track nêu đau ngực và khó thở là dấu hiệu nguy hiểm cần khuyên đi cấp cứu, không để khách chờ trong hàng đợi. |

### 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

1. Đau ngực và khó thở: AI có thể khiến khách hàng chậm cấp cứu nếu tư vấn như một yêu cầu mua thuốc bình thường. Hậu quả có thể nghiêm trọng và không thể khắc phục chỉ bằng cách sửa câu trả lời sau đó.
2. Trẻ bị sốt nhưng thiếu thông tin: AI có thể đề xuất thuốc không phù hợp hoặc đưa ra hướng dẫn sai khi chưa biết tuổi, cân nặng và dấu hiệu nguy hiểm. Một khi thuốc đã được sử dụng, không thể đơn giản hoàn tác.

## §3. Khi AI sai  (chặng 3)

### Kịch bản 1 — Khách hàng có dấu hiệu cấp cứu

Mức độ: `Không chấp nhận được`
Tin nhắn người dùng:
"Mẹ tôi bị đau ngực và hơi khó thở từ sáng. Có thuốc gì uống đỡ không?"

 **1. AI nói gì, người dùng thấy gì, làm gì tiếp?**


> > Hãy tìm trợ giúp y tế ngay
> > "Đau ngực kèm khó thở có thể là dấu hiệu của tình trạng nghiêm trọng. Trường hợp này không nên tự mua thuốc để xử lý tại nhà.
> > Vui lòng gọi 115 hoặc đưa mẹ bạn đến cơ sở cấp cứu gần nhất ngay bây giờ. Đừng chờ dược sĩ phản hồi qua chat.
> > Mình sẽ không đề xuất thuốc trong tình huống này để tránh làm chậm việc cấp cứu."

*Làm gì tiếp?*
- AI dừng luồng tư vấn và không gọi `goi_y_san_pham`.
- AI kích hoạt `khuyen_di_kham` ngay lập tức.
- Không đưa khách vào hàng chờ `chuyen_duoc_si` như bước xử lý chính.
- Hiển thị lại cảnh báo nếu khách tiếp tục hỏi mua thuốc.

**Ai được báo, sau bao lâu?**

| Người nhận                  | Thời điểm                     | Nội dung                                               |
| --------------------------- | ----------------------------- | ------------------------------------------------------ |
| Khách hàng                  | Ngay lập tức                  | Cảnh báo dấu hiệu nguy hiểm và hướng dẫn gọi 115       |
| Dược sĩ trực                | Ngay khi phát hiện tình huống | Thông báo ca có dấu hiệu cấp cứu để nắm được tình hình |
| Hệ thống giám sát hội thoại | Ngay khi kích hoạt cảnh báo   | Ghi nhận sự kiện để kiểm tra AI có xử lý đúng không    |

**2. Quyết định thiết kế**

`Chọn: Dừng và chuyển hướng xử lý khẩn cấp`

| Phương án            | Quyết định                       | Lý do                                                                                         |
| -------------------- | -------------------------------- | --------------------------------------------------------------------------------------------- |
| Hỏi lại              | Loại bỏ                          | Hỏi thêm nhiều câu có thể làm chậm việc tìm trợ giúp y tế.                                    |
| Trả lời kèm giới hạn | Loại bỏ                          | Một câu trả lời có giới hạn vẫn có thể khiến khách nghĩ rằng tự mua thuốc là phù hợp.         |
| Dừng và chuyển người | Chọn, kèm hướng dẫn cấp cứu ngay | Đây là tình huống có nguy cơ cao; khách cần được hướng dẫn hành động ngay thay vì chờ tư vấn. |

**3. Loại lỗi và cách xử lý**

- Loại lỗi: Lỗi ngữ cảnh (context error).
- Khách hàng hỏi mua thuốc, nhưng thông tin trong câu hỏi cho thấy đây có thể là tình huống cấp cứu. Nếu AI chỉ phân loại theo ý định mua thuốc mà bỏ qua triệu chứng, nó sẽ hiểu sai ngữ cảnh.
- Cách nói phải ưu tiên sự khẩn cấp, rõ ràng và trực tiếp. Cách sửa không phải là hỏi khách cung cấp thêm thông tin, mà là ngừng luồng bán hàng và hướng dẫn hành động an toàn.

**4. Nguyên tắc HAX/PAIR áp dụng**

| Nguyên tắc                               | Áp dụng cụ thể                                                                                                             |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| HAX G10 - Narrow scope under uncertainty | AI không đưa ra đề xuất thuốc khi gặp dấu hiệu có thể nguy hiểm; chỉ hướng dẫn tìm trợ giúp y tế.                          |
| HAX G11 – Explain why                    | Câu "Đau ngực kèm khó thở có thể là dấu hiệu của tình trạng nghiêm trọng" giải thích lý do AI dừng tư vấn thuốc.           |
| PAIR – Errors and graceful failure       | Khi không thể xử lý an toàn, AI chuyển sang một luồng xử lý khác thay vì cố gắng trả lời hoặc đưa ra đề xuất thiếu căn cứ. |

**5. Lỗi không thể sửa chỉ bằng câu chữ**

Lỗi: AI nhận diện sai dấu hiệu cấp cứu và vẫn gọi `goi_y_san_pham` hoặc đưa khách vào hàng chờ dược sĩ.
Chỉ thay câu trả lời thành "Tôi không chắc chắn" không giải quyết được vấn đề.
Thiết kế cứu lỗi:

- Tạo quy tắc ưu tiên nhận diện dấu hiệu nguy hiểm trước khi xử lý ý định mua thuốc.
- Chặn `goi_y_san_pham` khi phát hiện dấu hiệu cấp cứu.
- Kích hoạt `khuyen_di_kham` ngay khi phát hiện tình huống phù hợp.
- Kiểm thử các câu hỏi có triệu chứng cấp cứu nhưng được diễn đạt như yêu cầu mua thuốc thông thường.

### Kịch bản 2 — Trẻ bị sốt nhưng thiếu thông tin

Mức độ: `Không chấp nhận được`
Tin nhắn người dùng:
"Con mình sốt, mình chỉ cần biết có thuốc gì dùng được ngay, đừng bắt mình chờ dược sĩ."

1. AI nói gì, người dùng thấy gì, làm gì tiếp?

> > Mình cần xác nhận một vài thông tin để đảm bảo an toàn
> > "Mình hiểu bạn đang cần hỗ trợ nhanh cho bé.
> > Vì thuốc dành cho trẻ em cần được lựa chọn cẩn thận, mình chưa thể đề xuất sản phẩm khi chưa biết thêm thông tin.
> > Bé hiện bao nhiêu tuổi?"
> >
> > Người dùng thấy các lựa chọn:
> >
> > - Dưới 2 tuổi
> > - Từ 2 đến dưới 6 tuổi
> > - Từ 6 đến dưới 12 tuổi
> > - Từ 12 tuổi trở lên
> > - Không chắc chắn
> >   Đây là ví dụ giao diện hỏi thông tin. Các lựa chọn tuổi chỉ phục vụ sàng lọc ban đầu, không thay thế đánh giá chuyên môn.

*Làm gì tiếp?*
- Sau khi khách trả lời, AI tiếp tục hỏi cân nặng, nhiệt độ và các triệu chứng cần thiết, từng câu một.
- Nếu phát hiện dấu hiệu nguy hiểm, AI dừng việc hỏi thông tin thông thường và hướng dẫn tìm trợ giúp y tế khẩn cấp.
- Nếu chưa có dấu hiệu cấp cứu nhưng vẫn thiếu thông tin hoặc cần đánh giá chuyên môn, AI gọi `chuyen_duoc_si`.

*Ai được báo, sau bao lâu?*
| Người nhận | Thời điểm | Nội dung |
| --- | --- | --- |
| Khách hàng | Ngay khi AI xác định thiếu thông tin | Lý do cần hỏi thêm và câu hỏi tiếp theo |
| Dược sĩ trực | Ngay khi AI chuyển ca | Tin nhắn ban đầu và các thông tin khách đã cung cấp |
| Dược sĩ trực | Mục tiêu xác nhận tiếp nhận trong 2 phút | Xác nhận đang tiếp nhận ca; nếu chưa có người nhận, khách được thông báo đang chờ và cách liên hệ khác |

**2. Quyết định thiết kế**

`Chọn: Hỏi lại trước, sau đó chuyển dược sĩ nếu cần`

| Phương án |Quyết định | Lý do |
| --- | --- | --- |
| Hỏi lại | Chọn | Tuổi, cân nặng và triệu chứng là dữ liệu quan trọng để đánh giá mức độ an toàn. |
| Trả lời | Kèm giới hạn | Loại bỏ việc gợi ý thuốc ngay. AI chưa đủ thông tin để đề xuất sản phẩm cho trẻ. |
| Dừng và chuyển người | Chọn khi thiếu thông tin quan trọng, có dấu hiệu nguy hiểm hoặc cần chuyên môn | Đảm bảo trẻ không nhận đề xuất thiếu căn cứ. |

*Tại sao không hỏi tất cả thông tin cùng lúc?* : Khách hàng đang lo lắng và muốn được hỗ trợ nhanh. Hỏi từng câu ngắn giúp giảm tải nhận thức và tăng khả năng khách cung cấp thông tin chính xác.

**3. Loại lỗi và cách xử lý**
Loại lỗi: Lỗi ngữ cảnh (context error) kết hợp với thiếu dữ liệu đầu vào.

Người nhắn tin là phụ huynh, nhưng người trực tiếp sử dụng thuốc là trẻ nhỏ. Nếu AI mặc định người nhắn và người uống thuốc là cùng một người, nó có thể áp dụng sai thông tin hoặc đề xuất không phù hợp.

Cách nói cần thể hiện rằng AI đang hỏi để bảo vệ trẻ, không phải cố tình gây khó dễ. Cách sửa là xác định người sử dụng thuốc và thu thập dữ liệu còn thiếu trước khi quyết định có thể tiếp tục hỗ trợ hay cần chuyển dược sĩ.

**4. Nguyên tắc HAX/PAIR áp dụng**
| Nguyên tắc | Áp dụng cụ thể |
|---|---|
| HAX G1 – Make clear what the system can do | AI nói rõ mình chưa thể đề xuất thuốc khi chưa có đủ thông tin về trẻ. |
| HAX G11 – Explain why | Câu "Vì thuốc dành cho trẻ em cần được lựa chọn cẩn thận" giải thích lý do hỏi tuổi. |
| HAX G15 – Provide feedback on actions | Khi chuyển dược sĩ, giao diện thông báo đã chuyển ca và cho khách biết trạng thái tiếp nhận. |

**5. Lỗi không thể sửa chỉ bằng câu chữ**
Lỗi: AI không xác định được người trực tiếp sử dụng thuốc hoặc tự suy đoán tuổi, cân nặng của trẻ.

Việc thêm câu "Thông tin chỉ mang tính tham khảo" không làm cho một đề xuất thuốc thiếu dữ liệu trở nên an toàn.

Thiết kế cứu lỗi:
- Bắt buộc xác định người sử dụng thuốc trước khi gợi ý sản phẩm.
- Không cho phép gọi `goi_y_san_pham` khi thiếu thông tin an toàn bắt buộc.
- Nếu khách không muốn cung cấp thông tin, cho phép chuyển dược sĩ thay vì ép khách trả lời.
- Nếu phát hiện dấu hiệu cấp cứu, ưu tiên `khuyen_di_kham`, không tiếp tục quy trình sàng lọc thông thường.
- Kiểm thử trường hợp người nhắn là phụ huynh nhưng người sử dụng thuốc là trẻ nhỏ.



## §4. Mức tự chủ  (chặng 4)

### 4.1. Quyết định mức tự chủ cho từng công cụ

| Công cụ | Mức tự chủ | Ai phê duyệt? | Lý do và rủi ro nếu sai |
|---|---|---|---|
| `goi_y_san_pham` | **Cần người duyệt** | Dược sĩ đang trực | Gợi ý sai thuốc có thể khiến khách hàng sử dụng sản phẩm không phù hợp. Khi thuốc đã được sử dụng, hậu quả khó đảo ngược. Việc chờ dược sĩ duyệt có thể làm khách hàng phải đợi lâu hơn. |
| `chuyen_duoc_si` | **Tự làm** | Không cần phê duyệt trước | AI có thể tự chuyển cuộc trò chuyện khi thiếu thông tin quan trọng, gặp nhóm khách hàng có nguy cơ cao hoặc cần chuyên môn. Chuyển nhầm chủ yếu gây mất thời gian của dược sĩ và có thể xử lý lại. Nếu phải chờ phê duyệt, khách hàng có thể bị chậm hỗ trợ. |
| `khuyen_di_kham` | **Tự làm** | Không cần phê duyệt trước | Khi phát hiện dấu hiệu nguy hiểm, AI cần cảnh báo và hướng dẫn khách hàng tìm trợ giúp y tế ngay. Nếu bỏ sót cảnh báo, hậu quả có thể nghiêm trọng và khó đảo ngược. Cảnh báo nhầm thường ít nguy hiểm hơn việc bỏ sót tình huống khẩn cấp. |
| `luu_ghi_chu_suc_khoe` | **Cần người duyệt** | Khách hàng | Khách hàng phải được xem chính xác thông tin nào sẽ được lưu và chủ động đồng ý. Thông tin sức khỏe là dữ liệu riêng tư; xóa sau đó không thể hoàn toàn đảo ngược việc thông tin đã bị tiết lộ. Nếu khách hàng không đồng ý, hệ thống không được lưu. |
| `ban_thuoc_ke_don` | **Cấm** | Không áp dụng trong phạm vi AI | AI không được tự bán thuốc kê đơn qua chat. Đây là hành động nằm ngoài quyền hạn của tính năng AI trong bài tập. Việc khách hàng bấm đồng ý không thay thế các yêu cầu chuyên môn hoặc quy định liên quan. Điều này không có nghĩa là dược sĩ không thể xử lý đơn thuốc hợp lệ qua quy trình riêng bên ngoài AI. |

#### Thời hạn chờ phê duyệt (đề xuất)

| Công cụ | Người duyệt nhìn thấy gì? | Nếu quá thời hạn mà chưa duyệt |
|---|---|---|
| `goi_y_san_pham` | Tin nhắn khách hàng, người sẽ sử dụng thuốc, thông tin sàng lọc, sản phẩm được đề xuất, thành phần, lý do đề xuất và cảnh báo liên quan. | Nếu sau **2 phút** chưa có dược sĩ duyệt, AI không gửi gợi ý sản phẩm và không hiển thị nút đặt hàng. AI thông báo khách hàng đang chờ dược sĩ và cho phép khách hàng tiếp tục chờ hoặc tìm trợ giúp y tế phù hợp. |
| `luu_ghi_chu_suc_khoe` | Nội dung sức khỏe cụ thể sẽ lưu, mục đích lưu và nơi lưu. | Nếu khách hàng không xác nhận rõ ràng, hệ thống không lưu. Im lặng không được xem là đồng ý. |
| `ban_thuoc_ke_don` | Không có người duyệt trong luồng AI vì công cụ này bị cấm đối với AI. | AI không thực hiện hành động này. Nếu khách hàng có đơn thuốc hợp lệ, dược sĩ có thể xử lý theo quy trình riêng bên ngoài luồng AI. |

### 4.2. Công cụ gây tranh luận nhiều nhất: `goi_y_san_pham`

#### Quyết định

Chọn mức **Cần người duyệt**, đồng thời tách công việc thành hai bước:

1. AI chuẩn bị bản nháp gợi ý sản phẩm dựa trên thông tin khách hàng cung cấp.
2. Dược sĩ kiểm tra, chỉnh sửa nếu cần và phê duyệt trước khi gửi gợi ý cho khách hàng kèm nút đặt hàng.

#### Đánh đổi được cân nhắc

- Nếu để AI tự gửi, khách hàng được phản hồi nhanh nhưng nguy cơ gợi ý sai cho trẻ em hoặc người có yếu tố nguy cơ cao sẽ tăng.
- Nếu yêu cầu dược sĩ duyệt, độ an toàn cao hơn nhưng khách hàng phải chờ.
- Nếu cấm hoàn toàn, AI không thể hỗ trợ cả những câu hỏi đơn giản, làm tăng tải cho dược sĩ.

### 4.3. Kiểm tra mức tự chủ qua ba tình huống

#### Tình huống A – Khách hàng có dấu hiệu cấp cứu

**Tin nhắn:** "Mẹ tôi bị đau ngực và khó thở, có thuốc nào uống được không?"

- AI tự động gọi `khuyen_di_kham`.
- AI hướng dẫn khách hàng gọi 115 hoặc đến cơ sở cấp cứu gần nhất.
- AI không gọi `goi_y_san_pham`.
- AI không yêu cầu khách hàng chờ trong hàng đợi tư vấn dược sĩ.
- Dược sĩ trực được thông báo về tình huống để có thể theo dõi cuộc trò chuyện.

**Rủi ro được kiểm soát:** AI không biến một tình huống có dấu hiệu nguy hiểm thành một yêu cầu mua thuốc thông thường.

**Thời gian chờ:** Không phải chờ dược sĩ mới nhận được cảnh báo khẩn cấp.

#### Tình huống B – Phụ huynh hỏi thuốc hạ sốt cho trẻ

**Tin nhắn:** "Con tôi bị sốt, tư vấn thuốc cho cháu ngay được không?"

- AI hỏi tuổi của người sẽ sử dụng thuốc trước.
- AI tiếp tục thu thập thông tin cần thiết như cân nặng, nhiệt độ và triệu chứng đi kèm.
- Nếu phát hiện dấu hiệu nguy hiểm, AI ưu tiên gọi `khuyen_di_kham`.
- Nếu thiếu thông tin quan trọng hoặc cần đánh giá chuyên môn, AI gọi `chuyen_duoc_si`.
- AI không tự gửi gợi ý sản phẩm hoặc nút đặt hàng khi chưa đủ thông tin và chưa có dược sĩ phê duyệt.

**Rủi ro được kiểm soát:** AI không mặc định người đang chat cũng chính là người sử dụng thuốc và không tự suy đoán tuổi, cân nặng hoặc liều dùng của trẻ.

**Thời gian chờ:** Khách hàng có thể phải chờ dược sĩ trong trường hợp cần tư vấn chuyên môn, nhưng không phải chờ mới nhận được hướng dẫn khẩn cấp nếu có dấu hiệu nguy hiểm.

#### Tình huống C – Khách hàng hỏi thông tin OTC thông thường

**Tin nhắn:** "Sản phẩm này có thành phần gì và quy cách đóng gói như thế nào?"

- Nếu thông tin có trong danh mục sản phẩm đã được xác minh, AI có thể trả lời trực tiếp.
- AI không cần gọi `goi_y_san_pham` nếu khách hàng chỉ hỏi thông tin sản phẩm.
- AI không cần chuyển dược sĩ nếu câu hỏi nằm trong phạm vi thông tin đã xác minh.
- Nếu không có dữ liệu hoặc không xác minh được thông tin, AI phải nói rõ thay vì tự suy đoán.

**Rủi ro được kiểm soát:** AI không đưa ra thông tin không có căn cứ và không chuyển mọi câu hỏi đơn giản sang dược sĩ.

**Thời gian chờ:** Khách hàng nhận được câu trả lời ngay nếu thông tin có sẵn và đã được xác minh.

#### Tổng hợp kết quả kiểm tra

| Tình huống | Hành động của AI | Có cần dược sĩ duyệt? | Rủi ro chính được kiểm soát |
|---|---|---|---|
| Đau ngực, khó thở | Tự động hướng dẫn cấp cứu | Không cần chờ duyệt | Không trì hoãn hỗ trợ khẩn cấp |
| Trẻ bị sốt | Hỏi thêm thông tin, chuyển dược sĩ khi cần | Có, trước khi gửi gợi ý sản phẩm | Không tư vấn thuốc khi thiếu dữ liệu về trẻ |
| Hỏi thông tin OTC thông thường | Trả lời từ danh mục đã xác minh | Không | Không gây chờ đợi không cần thiết |

### 4.4. Quy tắc mới và đề xuất tách công cụ

Đề xuất tách `goi_y_san_pham` thành hai công cụ nhỏ hơn để phân định rõ trách nhiệm giữa AI và dược sĩ.

| Công cụ đề xuất | Mức tự chủ | Chức năng |
|---|---|---|
| `soan_goi_y_san_pham` | **Tự làm** | AI chuẩn bị bản nháp nội bộ gồm tên sản phẩm, thành phần, lý do đề xuất, thông tin an toàn, cảnh báo và dữ liệu còn thiếu. Bản nháp chưa được gửi cho khách hàng và không có nút đặt hàng. |
| `gui_goi_y_san_pham` | **Cần người duyệt** | Dược sĩ xem bản nháp, chỉnh sửa nếu cần và phê duyệt trước khi gửi gợi ý sản phẩm cho khách hàng kèm nút đặt hàng. |

#### Các quy tắc bổ sung

1. AI không được soạn gợi ý sản phẩm nếu chưa xác định được người sẽ sử dụng thuốc.
2. Nếu phát hiện dấu hiệu cấp cứu, AI không được soạn gợi ý sản phẩm mà phải ưu tiên `khuyen_di_kham`.
3. Không gửi gợi ý sản phẩm hoặc nút đặt hàng cho khách hàng trước khi dược sĩ phê duyệt.
4. Nếu thông tin sản phẩm thiếu hoặc chưa được xác minh, AI phải thông báo rõ và không tự suy đoán.
5. AI không được gọi `luu_ghi_chu_suc_khoe` nếu khách hàng chưa chủ động đồng ý.

### 4.5. Thay đổi lời hứa với người dùng

#### Lời hứa ban đầu

"AI sẽ chọn và đề xuất sản phẩm phù hợp cho bạn ngay lập tức."

#### Lời hứa sau khi điều chỉnh

"Trợ lý AI Pharmacity giúp bạn tìm thông tin và chuẩn bị tư vấn nhanh chóng. Với những đề xuất thuốc cần đánh giá chuyên môn, dược sĩ sẽ kiểm tra trước khi gửi đến bạn. Nếu phát hiện dấu hiệu nguy hiểm, hệ thống sẽ ưu tiên hướng dẫn bạn tìm trợ giúp y tế thay vì yêu cầu bạn chờ tư vấn."

#### Lý do thay đổi

- Không hứa rằng AI luôn có thể tự chọn thuốc phù hợp.
- Minh bạch về vai trò của AI và dược sĩ.
- Đặt an toàn của khách hàng lên trước tốc độ đề xuất sản phẩm.
- Giúp khách hàng hiểu khi nào AI có thể trả lời trực tiếp và khi nào cần chuyển cho dược sĩ.

## §5. Prototype  (chặng 5)

### 5.1. Prototype overview

#### Ca được chọn

**Khách hàng hỏi mua thuốc cho mẹ đang bị đau ngực và khó thở.**

Tin nhắn khách hàng:

> "Mẹ tôi bị đau ngực và khó thở, có thuốc nào uống được không?"

Đây là tình huống có nguy cơ cao. AI phải nhận diện dấu hiệu nguy hiểm dù khách hàng đang diễn đạt nhu cầu dưới dạng hỏi mua thuốc.

#### Mục tiêu prototype

Prototype tập trung thể hiện ba quyết định:

1. AI tự động cảnh báo và hướng dẫn khách hàng tìm trợ giúp y tế khẩn cấp.
2. AI không tự gửi gợi ý sản phẩm; đề xuất sản phẩm phải được dược sĩ phê duyệt.
3. AI không thực hiện hành động bán thuốc kê đơn trong luồng chat.

Prototype gồm **2 màn hình chính**, sử dụng dữ liệu giả, không cần đăng nhập hoặc backend.

---

### 5.2. Hai màn hình prototype

#### Màn hình 1 – Khách hàng chat với AI

**Mục đích:** Cho thấy AI nhận diện tình huống nguy hiểm, giải thích giới hạn và tự thực hiện hành động phù hợp.

**Các thành phần trên màn hình:**

- Tên trợ lý: Pharmacity AI.
- Tin nhắn của khách hàng: "Mẹ tôi bị đau ngực và khó thở, có thuốc nào uống được không?"
- Phản hồi của AI:

  > "Đau ngực kèm khó thở có thể là dấu hiệu nguy hiểm. Bạn hãy gọi 115 hoặc đưa mẹ đến cơ sở cấp cứu gần nhất ngay. Đừng chờ tư vấn thuốc qua chat."

- Nhãn trạng thái: "Ưu tiên an toàn – cần trợ giúp y tế khẩn cấp".
- Nút hành động:
  - "Gọi 115"
  - "Xem hướng dẫn cấp cứu"
- Thông báo trạng thái:
  - "Đã gửi cảnh báo đến dược sĩ trực."
  - "Bạn không cần chờ dược sĩ mới nhận được hướng dẫn khẩn cấp."

**Hành vi khi bấm:**

| Người dùng bấm | Kết quả |
|---|---|
| Gọi 115 | Hiển thị hướng dẫn gọi cấp cứu. Nếu prototype chạy trên thiết bị hỗ trợ liên kết gọi điện, có thể mở trình gọi điện. |
| Xem hướng dẫn cấp cứu | Hiển thị hướng dẫn ngắn gọn về việc tìm trợ giúp y tế khẩn cấp. |
| Tiếp tục hỏi mua thuốc | AI giải thích rằng không thể đề xuất thuốc trong tình huống có dấu hiệu nguy hiểm. |

**Mức tự chủ được thể hiện:**

- `khuyen_di_kham`: **Tự làm** – AI tự động cảnh báo, không cần chờ phê duyệt.
- `chuyen_duoc_si`: **Tự làm** – AI thông báo cho dược sĩ trực để theo dõi.
- `goi_y_san_pham`: **Không thực hiện** – AI không đưa ra gợi ý thuốc trong tình huống này.

#### Màn hình 2 – Góc nhìn kiểm tra của dược sĩ

**Mục đích:** Cho thấy dược sĩ được thông báo về tình huống nguy hiểm và có thể xem lý do AI dừng đề xuất sản phẩm.

**Các thành phần trên màn hình:**

- Tiêu đề: "Thông báo cuộc trò chuyện cần chú ý".
- Tin nhắn khách hàng.
- Dấu hiệu được AI nhận diện:
  - Đau ngực.
  - Khó thở.
- Lý do chuyển hướng:
  - "Có dấu hiệu nguy hiểm. Ưu tiên hướng dẫn cấp cứu thay vì tư vấn sản phẩm."
- Trạng thái hành động:
  - `khuyen_di_kham`: Đã thực hiện.
  - `chuyen_duoc_si`: Đã thông báo.
  - `goi_y_san_pham`: Bị chặn.
  - `ban_thuoc_ke_don`: Không được phép trong luồng AI.

**Các nút trên màn hình:**

- "Xác nhận đã nhận thông báo"
- "Xem nội dung cuộc trò chuyện"

**Hành vi khi bấm:**

| Người dùng bấm | Kết quả |
|---|---|
| Xác nhận đã nhận thông báo | Trạng thái chuyển thành "Dược sĩ đã tiếp nhận". |
| Xem nội dung cuộc trò chuyện | Hiển thị tin nhắn khách hàng và phản hồi AI. |

**Lưu ý:** Dược sĩ tiếp nhận thông báo không có nghĩa là khách hàng phải chờ dược sĩ trước khi tìm trợ giúp y tế.

---

### 5.3. AI thể hiện mức độ chắc chắn và căn cứ như thế nào?

Prototype không sử dụng phần trăm độ chính xác vì nhóm không có dữ liệu để chứng minh một con số cụ thể.

Thay vào đó, AI thể hiện mức độ chắc chắn bằng ngôn ngữ rõ ràng:

| Nội dung | Cách thể hiện |
|---|---|
| Dấu hiệu nhận diện | "Bạn vừa mô tả đau ngực và khó thở." |
| Lý do cảnh báo | "Hai triệu chứng này có thể là dấu hiệu nguy hiểm." |
| Giới hạn của AI | "Tôi không thể xác định nguyên nhân hoặc chẩn đoán qua chat." |
| Hành động tiếp theo | "Hãy gọi 115 hoặc đến cơ sở cấp cứu gần nhất ngay." |

AI không khẳng định khách hàng đang mắc một bệnh cụ thể. AI giải thích rằng tổ hợp triệu chứng được mô tả đủ đáng lo ngại để ưu tiên tìm trợ giúp y tế.

---

### 5.4. Các mức tự chủ được thể hiện trên màn hình

| Mức tự chủ | Công cụ | Cách người dùng nhìn thấy |
|---|---|---|
| Tự làm | `khuyen_di_kham` | AI tự hiển thị cảnh báo và hướng dẫn cấp cứu ngay trong màn hình chat. |
| Tự làm | `chuyen_duoc_si` | AI hiển thị thông báo đã chuyển tình huống cho dược sĩ trực. |
| Cần người duyệt | `gui_goi_y_san_pham` | Ở màn hình dược sĩ, bản nháp phải được dược sĩ kiểm tra và phê duyệt trước khi gửi cho khách hàng. Không xuất hiện nút đặt hàng trước khi duyệt. |
| Cấm | `ban_thuoc_ke_don` | AI từ chối thực hiện và hướng khách hàng đến quy trình phù hợp với dược sĩ. |

#### Hoàn tác và xử lý khi AI làm sai

- Với `khuyen_di_kham`: Không có nút hoàn tác cảnh báo đã gửi. Nếu nhận diện nhầm, dược sĩ có thể xem lại và giải thích với khách hàng. Không xóa cảnh báo đã gửi để tránh che giấu lịch sử xử lý.
- Với `chuyen_duoc_si`: Có thể cập nhật trạng thái tiếp nhận hoặc kết thúc chuyển tiếp nếu xác định không cần theo dõi thêm.
- Với gợi ý sản phẩm: Dược sĩ có thể chỉnh sửa hoặc từ chối bản nháp trước khi gửi. Nếu đã gửi, cần có quy trình đính chính riêng.
- Với bán thuốc kê đơn: Không có nút cho phép AI vượt qua giới hạn này.

---

### 5.5. Nguyên tắc HAX/PAIR xuất hiện ở đâu?

| Nguyên tắc | Vị trí trong prototype | Cách thể hiện |
|---|---|---|
| HAX G1 – Make clear what the system can do | Màn hình 1 | AI nói rõ không thể chẩn đoán hoặc xác định nguyên nhân qua chat. |
| HAX G10 – Narrow scope under uncertainty | Màn hình 1 | AI không đề xuất sản phẩm khi phát hiện dấu hiệu nguy hiểm. |
| HAX G11 – Explain why | Màn hình 1 | AI giải thích vì sao đau ngực kèm khó thở cần được ưu tiên xử lý. |
| HAX G15 – Provide feedback on actions | Cả hai màn hình | Khách hàng thấy thông báo đã gửi cảnh báo; dược sĩ thấy trạng thái tiếp nhận. |
| PAIR – Errors and graceful failure | Cả hai màn hình | Khi tình huống vượt quá phạm vi tư vấn thuốc, AI không cố trả lời mà chuyển sang hướng xử lý an toàn. |

---

### 5.6. Khi gặp tình huống lạ chưa được chuẩn bị

Prototype áp dụng nguyên tắc **không tự suy đoán khi thiếu thông tin hoặc không chắc chắn về phạm vi xử lý**.

Quy trình dự kiến:

1. AI kiểm tra xem tin nhắn có dấu hiệu nguy hiểm hay không.
2. Nếu có dấu hiệu nguy hiểm, ưu tiên `khuyen_di_kham`.
3. Nếu không có dấu hiệu nguy hiểm nhưng thiếu dữ liệu quan trọng, AI hỏi thêm hoặc gọi `chuyen_duoc_si`.
4. Nếu yêu cầu nằm ngoài phạm vi được phép, AI giải thích giới hạn và không thực hiện hành động đó.
5. AI không tự gọi công cụ bán thuốc hoặc gửi gợi ý sản phẩm khi chưa đủ điều kiện.

Ví dụ: Khách hàng gửi ảnh nhiều loại thuốc và hỏi có thể uống cùng nhau không. Nếu hệ thống không xác minh được đầy đủ tên thuốc, thành phần và tương tác, AI không tự kết luận an toàn. AI giải thích giới hạn và chuyển dược sĩ.

---

### 5.7. Các phương án thiết kế đã cân nhắc

| Phương án | Ưu điểm | Lý do không chọn |
|---|---|---|
| AI trả lời và đề xuất thuốc ngay trong chat | Nhanh, ít thao tác | Không an toàn khi khách hàng có dấu hiệu nguy hiểm. |
| Chỉ hiển thị thông báo "Hãy liên hệ dược sĩ" | Dễ làm, đơn giản | Có thể khiến khách hàng chờ dược sĩ thay vì tìm trợ giúp khẩn cấp. |
| AI cảnh báo ngay và thông báo dược sĩ song song | Ưu tiên an toàn, thể hiện rõ mức tự chủ và trách nhiệm của AI | Được chọn vì phù hợp với tình huống nguy hiểm và quyết định ở chặng 3–4. |

---

#### Tiêu chí hoàn thành M3

- [x] Có 1–2 màn hình prototype.
- [x] Bấm qua được tình huống đau ngực và khó thở.
- [x] Thể hiện ít nhất hai mức tự chủ khác nhau.
- [x] Người dùng nhìn thấy lý do AI cảnh báo và hành động tiếp theo.
- [x] Dược sĩ nhìn thấy thông báo và lý do AI không đề xuất sản phẩm.
- [x] Mỗi nguyên tắc HAX/PAIR được chỉ ra tại một vị trí cụ thể.
- [x] Có đường xử lý khi AI gặp tình huống chưa được chuẩn bị.
- [x] Có thể demo trong 4 phút.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)

- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo

- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
