# CardDeals MCP Server [![MCP](https://img.shields.io/badge/MCP-Streamable%20HTTP-blue?style=for-the-badge)](https://carddeals.co/mcp) [![Website](https://img.shields.io/badge/Website-carddeals.co-00D084?style=for-the-badge)](https://carddeals.co/mcp) [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

Official Model Context Protocol (MCP) server for **[CardDeals](https://carddeals.co)** — query and compare real-time discounted digital gift cards across 700+ top retail, dining, travel, and entertainment brands directly inside AI assistants (Claude, Cursor, ChatGPT, and autonomous purchasing agents).

* 🌐 **Landing Page & Documentation:** [https://carddeals.co/mcp](https://carddeals.co/mcp)
* ⚡ **Remote MCP Endpoint:** `https://catalog.carddeals.co/mcp`
* 📑 **OpenAPI REST Specification:** [https://catalog.carddeals.co/openapi.json](https://catalog.carddeals.co/openapi.json)
* 📋 **Registry Metadata:** [https://catalog.carddeals.co/mcp/server.json](https://catalog.carddeals.co/mcp/server.json)

---

## 🚀 Key Features

* **Anonymous & Free:** No authentication, account creation, or API keys required during public beta.
* **Safe & Read-Only:** Exposes discovery and price comparison tools with zero mutation or direct checkout permissions.
* **Streamable HTTP:** Modern remote MCP transport compatible with Claude Desktop, Cursor, and standard MCP clients.
* **Real-Time Data:** Live discount rates, seller observation timestamps, and condition disclosures across secondary marketplaces.

---

## 🛠️ Available MCP Tools

| Tool | Description | Example Query |
|---|---|---|
| `search_gift_card_deals` | Search current discounts by brand text or category (Food, Retail, Travel, Tech, Fashion). Returns up to 10 products. | *"Find dining deals for date night"* |
| `get_gift_card_deals` | Retrieve all current validated offers, sellers, and conditions for a specific brand slug or product ID. | *"Get current Starbucks gift card deals"* |
| `lookup_gift_card_deals` | Batch resolve up to 10 brand slugs or product IDs in a single call. | *"Check discounts for Apple, Target, and Airbnb"* |

---

## ⚙️ Client Quickstart

### 1. Claude Desktop

Add the following to your `claude_desktop_config.json`:

* **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
* **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "carddeals": {
      "type": "http",
      "url": "https://catalog.carddeals.co/mcp"
    }
  }
}
```

### 2. Cursor IDE

Add to your project's `.cursor/mcp.json` or global MCP settings:

```json
{
  "mcpServers": {
    "carddeals": {
      "type": "http",
      "url": "https://catalog.carddeals.co/mcp"
    }
  }
}
```

### 3. REST / OpenAPI Alternative

If your agent framework prefers OpenAPI or REST tool calling:

```bash
# Search deals by brand
curl "https://catalog.carddeals.co/v1/deals/search?q=starbucks&limit=5"

# Get brand details
curl "https://catalog.carddeals.co/v1/deals/brands/starbucks"

# Batch lookup
curl "https://catalog.carddeals.co/v1/deals/lookup?ids=starbucks,target,airbnb"
```

---

## 🔒 Safety & Freshness Rules

* **Freshness:** Deals, discounts, and inventory fluctuate constantly. Tools return observation timestamps (`fetched_at`) and assembly timestamps (`as_of`).
* **Validation:** Recheck the destination seller before completing a purchase.
* **Disclosures:** Third-party affiliate links and CardDeals-owned inventory are clearly labeled in response metadata.

---

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
