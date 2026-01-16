# Template Registry Specification

## ADDED Requirements

### Requirement: Registry 檔案必須存在於專案根目錄

專案根目錄 SHALL 包含名為 [`registry.json`](../../../../registry.json:1) 的檔案,作為模板註冊表,供外部工具(如 start-ts-by)發現和使用專案中的模板。

#### Scenario: 外部工具讀取 registry.json

- **WHEN** 外部工具(如 start-ts-by)需要發現可用的模板時
- **THEN** 必須能在專案根目錄找到 [`registry.json`](../../../../registry.json:1) 檔案

#### Scenario: 專案初始化時驗證 registry 存在

- **WHEN** 專案進行初始化或建置檢查時
- **THEN** 必須確認 [`registry.json`](../../../../registry.json:1) 檔案存在且格式正確

### Requirement: Registry 必須包含必要欄位

[`registry.json`](../../../../registry.json:1) 檔案 MUST 包含以下欄位:
- `repo`: 字串,表示 GitHub 倉儲路徑(格式: owner/repo)
- `defaultRef`: 字串,表示預設的 Git 參考(如分支名稱)
- `templates`: 陣列,包含所有可用的模板定義

#### Scenario: 驗證 registry 結構完整性

- **WHEN** 讀取 [`registry.json`](../../../../registry.json:1) 檔案時
- **THEN** 必須包含 `repo`、`defaultRef` 和 `templates` 三個必要欄位

#### Scenario: repo 欄位格式驗證

- **WHEN** 驗證 `repo` 欄位內容時
- **THEN** 必須符合 "owner/repo" 格式(例如: "royfw/start-ts-templates")

#### Scenario: defaultRef 欄位指向有效分支

- **WHEN** 驗證 `defaultRef` 欄位內容時
- **THEN** 必須是倉儲中存在的有效 Git 參考(如 "main" 或 "master")

### Requirement: 模板定義必須包含完整資訊

`templates` 陣列中的每個模板物件 MUST 包含以下欄位:
- `id`: 字串,模板的唯一識別碼(kebab-case 格式)
- `path`: 字串,模板在倉儲中的相對路徑
- `title`: 字串,模板的顯示名稱

#### Scenario: 驗證單一模板定義結構

- **WHEN** 讀取 `templates` 陣列中的模板定義時
- **THEN** 每個模板物件必須包含 `id`、`path` 和 `title` 三個欄位

#### Scenario: 模板 id 必須唯一

- **WHEN** 驗證 `templates` 陣列中的所有模板時
- **THEN** 所有模板的 `id` 欄位值必須唯一,不得重複

#### Scenario: 模板 path 必須指向存在的目錄

- **WHEN** 驗證模板的 `path` 欄位時
- **THEN** 該路徑在專案中必須存在且為有效的目錄

#### Scenario: 模板 id 使用 kebab-case 格式

- **WHEN** 驗證模板的 `id` 欄位格式時
- **THEN** 必須使用 kebab-case 格式(例如: "app-tsdown", "lib-esbuild")

### Requirement: Registry 必須維持與實際模板目錄的同步

[`registry.json`](../../../../registry.json:1) 中註冊的模板 SHALL 與 [`templates/`](../../../../templates) 目錄中實際存在的模板保持同步,確保外部工具能正確存取所有可用的模板。

#### Scenario: 新增模板時更新 registry

- **WHEN** 在 [`templates/`](../../../../templates) 目錄下新增新模板時
- **THEN** 必須在 [`registry.json`](../../../../registry.json:1) 的 `templates` 陣列中新增對應的模板定義

#### Scenario: 移除模板時更新 registry

- **WHEN** 從 [`templates/`](../../../../templates) 目錄中移除模板時
- **THEN** 必須從 [`registry.json`](../../../../registry.json:1) 的 `templates` 陣列中移除對應的模板定義

#### Scenario: 重新命名模板時更新 registry

- **WHEN** 重新命名 [`templates/`](../../../../templates) 目錄下的模板時
- **THEN** 必須更新 [`registry.json`](../../../../registry.json:1) 中對應模板的 `id` 和 `path` 欄位

### Requirement: Registry 檔案必須為有效的 JSON 格式

[`registry.json`](../../../../registry.json:1) 檔案 MUST 符合標準的 JSON 格式規範,確保可被程式正確解析。

#### Scenario: JSON 語法驗證

- **WHEN** 使用 JSON 解析器讀取 [`registry.json`](../../../../registry.json:1) 時
- **THEN** 檔案必須能成功解析,不產生語法錯誤

#### Scenario: JSON 格式化要求

- **WHEN** 編輯或生成 [`registry.json`](../../../../registry.json:1) 時
- **THEN** 必須使用適當的縮排(建議 2 空格)以保持可讀性