# Skill lấy từ bên ngoài

Mỗi skill giữ nguyên file `LICENSE` của repo gốc trong thư mục của nó. Nội dung đã được đọc hết
trước khi đưa vào (skill ngoài là dữ liệu không đáng tin — có thể chứa chỉ dẫn nhắm vào model).
Cập nhật từ upstream: tải bản mới ở đúng đường dẫn, đọc lại diff, áp lại phần "Đã sửa" bên dưới.

| Skill | Nguồn | Commit | License | Đã sửa |
|---|---|---|---|---|
| `verification-before-completion` | [obra/superpowers](https://github.com/obra/superpowers) `skills/verification-before-completion/SKILL.md` | `8ca22dba9a94f28898bbce59f2537ff4d87c747d` | MIT | Không |
| `source-driven-development` | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) `skills/source-driven-development/SKILL.md` | `2686b620fc1fed2e8f60c704839c766b8594c6b6` | MIT | Không |
| `debugging-and-error-recovery` | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) `skills/debugging-and-error-recovery/SKILL.md` | `2686b620fc1fed2e8f60c704839c766b8594c6b6` | MIT | Đổi `description` sang Flutter + REST; thêm mục "Flutter + REST: client hay backend?" |

`source-driven-development` và `debugging-and-error-recovery` nhắc tới skill `security-and-hardening` /
`test-driven-development` không có trong bundle này — chỉ là tham chiếu, không làm hỏng gì.

## Đã xem nhưng KHÔNG lấy

| Skill | Nguồn | Vì sao |
|---|---|---|
| `flutter-use-http-package`, `flutter-implement-json-serialization` | flutter/agent-plugins (chính thức, BSD-3) | Dạy package `http` + JSON viết tay + `FutureBuilder`, trái khuôn dio/retrofit/json_serializable/VM; mô tả lại bắt đúng mọi việc "gọi REST API" nên kéo agent sai hướng |
| `dart-run-static-analysis`, `dart-fix-runtime-errors` | flutter/agent-plugins | Xui `dart fix --apply` / `dart format .` cả repo và bật `strict-casts` → diff khổng lồ; mô tả `dart-fix-runtime-errors` lệch nội dung (nhắc tool MCP không có) |
| `dart-generate-test-mocks`, `dart-add-unit-test` | flutter/agent-plugins | Giả định inject qua constructor + `http.Client`; repo mẫu dùng GetIt và chưa có test. Xem lại khi team bắt đầu viết test |
| `flutter-retrofit-networking`, `flutter-error-handling`, `common-api-design` | HoangNguyen0403/agent-skills-standard (MIT) | Ép Clean Architecture + freezed + Either/BLoC ("không Dio toàn cục", bắt buộc repository layer) — trái khuôn repo. Đã rút ý `unknownEnumValue` vào `flutter-api` |
| `api-and-interface-design` | addyosmani/agent-skills | Viết cho phía server (TypeScript, idempotency key lưu DB), khuyên camelCase query/PATCH — trái hợp đồng backend .NET. Đã rút ý "timeout ≠ thất bại, đừng tự retry POST" vào `flutter-api` |
| `incremental-implementation` | addyosmani/agent-skills | Bắt commit sau mỗi lát — đụng luồng duyệt/một-nhánh-một-thay-đổi của bow; tham chiếu file không có |
