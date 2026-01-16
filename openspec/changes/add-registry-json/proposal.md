# Change: 增加 registry.json 供 start-ts-by 使用

## Why

為了讓 [`start-ts-by`](https://github.com/royfw/start-ts-by) 工具能夠發現和使用 start-ts-templates 專案中的模板,需要在根目錄提供一個標準化的 registry.json 檔案。這個檔案將作為模板註冊表,讓使用者可以透過 `npx start-ts-by` 命令快速建立基於這些模板的新專案。

目前 templates 目錄下有多個模板(app-tsdown, lib-tsdown 等),但缺乏統一的註冊機制,導致外部工具無法自動發現和使用這些模板。

## What Changes

- 在專案根目錄新增 [`registry.json`](registry.json) 檔案
- 定義模板註冊表結構,包含:
  - 倉儲資訊 (repo)
  - 預設分支 (defaultRef)
  - 模板清單 (templates),每個模板包含:
    - 唯一識別碼 (id)
    - 模板路徑 (path)
    - 顯示標題 (title)
- 初始註冊以下模板:
  - `app-tsdown`: App (tsdown) 應用程式模板
  - `lib-tsdown`: Library 函式庫模板

## Impact

### 受影響的 Specs
- **新增**: [`specs/template-registry`](specs/template-registry/spec.md) - 定義模板註冊表的規範

### 受影響的程式碼
- **新增**: [`registry.json`](registry.json) - 根目錄的模板註冊表檔案

### 相容性
- 此變更為**新增功能**,不影響現有功能
- 對現有模板結構無破壞性影響
- 純粹提供額外的發現機制給外部工具使用