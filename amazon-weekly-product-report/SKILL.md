---
name: amazon-weekly-product-report
description: "Use this skill whenever the user asks to write, improve, or structure Amazon weekly product reports, operation summaries, ad-review narratives, inventory updates, Vine/review updates, next-week action plans, anonymized reports, HTML reports, or Feishu/Lark-ready weekly report exports."
---

# Amazon Weekly Product Report

## When To Use
- 用户要写产品周报、运营周报、上周工作总结或下周计划。
- 用户提供销量、广告、库存、评价、退货、Vine 和动作记录。
- 用户要求“优化内容、补充逻辑、不要改大框架”。
- 用户需要把周报做成 HTML、脱敏版、飞书/多维文档可发布版本。

## Inputs
- Reporting period and product/ASIN.
- Sales, ad, inventory, review, return and logistics facts.
- Actions completed last week and decisions needed this week.
- Optional output preference: plain Markdown, polished HTML, anonymized HTML, Feishu/Lark export.

## Workflow
1. Start with the business conclusion, then support it with facts.
2. Use a clear top-down structure: conclusion first, then result, cause, exclusions, and next actions.
3. Separate data changes, cause interpretation, completed actions and next actions.
4. Call out inventory blockers, review signals, ad efficiency and conversion issues.
5. Preserve the user's existing structure when they ask for light optimization.
6. End with prioritized next-week actions and owner/status when possible.
7. If the user asks for HTML, build a readable report artifact instead of only returning Markdown.
8. If the user asks for Feishu/Lark export, prepare a Feishu-ready structure or use the available Lark/Feishu document tooling after confirming the target location.

## Output Options
- **Markdown report**: default when the user only asks for analysis or copy.
- **HTML report**: use when the user asks for “HTML”, “美观”, “报告页”, “可视化”, or “麦肯锡风格”. Prefer a consulting-report style: white background, deep blue header, clear metric cards, concise executive summary, ordered tables, and action list.
- **Anonymized report**: use when the user asks to脱敏, share externally, hide store/product/ASIN/SKU/campaign/search term details, or make a template/reference. Preserve all numeric business data unless the user asks otherwise.
- **Feishu/Lark export**: offer or perform only when requested. Confirm destination if needed, then export the finalized report content. Do not expose sensitive identifiers in the exported version unless the user explicitly wants the original names retained.

## Anonymization Rules
- Replace store name, product title, ASIN, SKU, campaign names, ad group names, search terms, and competitor ASINs with functional labels.
- Prefer advertising-context labels over vague placeholders:
  - 精准匹配活动 / 精准匹配词 A
  - 广泛匹配活动 / 广泛匹配词 B
  - 商品投放活动 / 商品投放对象 A
  - 自动投放活动
  - 需否定词根 X
- Keep dates, revenue, units, orders, sessions, clicks, spend, sales, ACoS, TACoS, CPC, CTR, CVR, inventory, and ranking numbers unchanged.
- State clearly that the report is anonymized and that numeric data is preserved.

## HTML Report Guidance
- Use a consulting-style layout for business reports: executive summary at the top, then metric cards, then detailed tables and actions.
- Make the executive summary top-down:
  - Core conclusion: one sentence.
  - Result: what changed.
  - Main cause: what explains the change.
  - Exclusions: what is unlikely to be the cause.
  - Next step: what to check or do next.
- Prefer deep blue, white, and light blue accents. Avoid decorative gradients, busy backgrounds, and playful labels.
- Keep labels professional and operational. Avoid invented labels such as “泛化词”; use terms like 精准匹配、广泛匹配、商品投放、自动投放.
- If using local HTML, create a standalone `.html` file with embedded CSS so it opens directly in a browser.

## Quality Checks
- Do not turn uncertain causes into facts.
- Do not bury the main conclusion in details.
- Mention data gaps if numbers are missing.
- In anonymized outputs, search the final artifact for original store names, product names, ASINs, SKUs, campaign names, search terms, and competitor identifiers.
- In HTML outputs, check that the main conclusion is readable without horizontal scrolling and that tables remain clear on typical desktop widths.

## Failure Handling
- If only rough notes are provided, keep the user's language where useful and polish structure.
- If no data exists, produce a qualitative report and list required metrics.
- If Feishu/Lark export tooling or destination is unavailable, provide the finalized Markdown/HTML content and state what is needed to complete the export.

## Example Triggers

> 优化这段周报内容，适当增减和补充逻辑，不要动大的框架和结构。

> 用 HTML 做美观一点，麦肯锡风格，报告脱敏。

> 生成一版可以发到飞书的周报。

## Final Response Style

- Be concise but operational.
- Put findings and recommended actions before background explanation.
- Use tables when comparing terms, products, competitors or action lists.
- Clearly label facts, assumptions, risks and next steps.
- When an artifact is created, return the local file path and summarize what was generated.