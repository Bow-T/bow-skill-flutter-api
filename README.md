# bow-skill-flutter-api

Bộ skill cho stack **Flutter + REST API** (app gọi backend riêng qua HTTP, không dùng Supabase),
dùng với [bow-agent](https://github.com/Bow-T/bow-agent). Khuôn:
dio + retrofit + json_serializable + `BaseResponse<T>` / `Pagination<T>` + mã lỗi server → l10n.

## Cấu trúc

```
bow-skill-flutter-api/
├── bow-skill.json                         # manifest — skillsDir "skills"
├── THIRD_PARTY.md                         # nguồn + commit + license skill lấy ngoài, và danh sách đã loại
└── skills/
    ├── flutter-api/                       # thêm/sửa endpoint REST + gọi từ ViewModel (của team)
    ├── debugging-and-error-recovery/      # addyosmani/agent-skills, chỉnh cho Flutter + REST
    ├── source-driven-development/         # addyosmani/agent-skills — bám tài liệu gốc đúng phiên bản
    └── verification-before-completion/    # obra/superpowers — bằng chứng trước khi báo xong
```

## Tự nhận diện

bow-agent tự tick bộ này cho dự án chưa khai công nghệ khi một `pubspec.yaml` đã track (ở gốc
hoặc thư mục con) có gói `retrofit` hoặc `dio` — dấu hiệu app gọi backend REST riêng theo khuôn mà
skill `flutter-api` mô tả. Quy tắc nằm ở `targets.detect` trong `bow-skill.json`.

Giới hạn: app gọi REST bằng gói `http` (chưa chuyển sang dio + retrofit) KHÔNG khớp — không có dấu
hiệu nào trong `pubspec.yaml` phân biệt nó với một app Flutter bất kỳ. Dự án như vậy tick bộ này bằng tay.

## Đăng ký vào bow-agent

Thêm vào `stacks` của `~/.bow-agent/registry.json`:

```json
{ "id": "flutter-api", "label": "Flutter + API", "repo": "github.com/Bow-T/bow-skill-flutter-api", "ref": "v1.1.0" }
```

Thử local trước khi đẩy GitHub: `"repo": "file:///đường/dẫn/tới/bow-skill-flutter-api"`.

## Phát hành phiên bản mới

Sửa skill → tăng `version` trong `bow-skill.json` → gắn tag (`git tag v1.0.1 && git push --tags`)
→ cập nhật `ref` trong registry. bow luôn tải theo tag và cache theo `<id>@<ref>`, nên sửa nội dung
mà giữ nguyên tag sẽ KHÔNG được tải lại.
