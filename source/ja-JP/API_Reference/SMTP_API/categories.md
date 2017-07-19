---
layout: page
weight: '0'
title: カテゴリ
navigation:
  show: 'true'
---

SendGrid経由で送信するメールのX-SMTPAPIヘッダに[カテゴリ](%7B%7Broot_url%7D%7D/User_Guide/Email_Settings/categories.html)を追加できます。こうすることでメールをカテゴライズしてトラッキングできます。

{% warning %}
カテゴリはUS-ASCII文字セットを使用した7bitエンコードである必要があります。
{% endwarning %}

{% info %}
現在のところ、トラッキング可能なカテゴリの数に制限はありませんが、ダッシュボードのStatsページの使い勝手を考慮して*ユニークカテゴリの合計が100を超えないこと*を推奨します。また、高頻度でユニークカテゴリが増加すると、メッセージ送信速度にネガティブな影響を与える可能性があります。
{% endinfo %}

{% warning %}
カテゴリはメッセージをグループ化する目的で使用されます。メッセージに一意のデータや識別子を追加する場合、代わりに[ユニーク引数](%7B%7Broot_url%7D%7D/API_Reference/SMTP_API/unique_arguments.html)を使用してください。
{% endwarning %}

{% anchor h2 %}
例
{% endanchor %}

メールにカテゴリを追加するのにSendGrid独自の[SMTP API](%7B%7Broot_url%7D%7D/API_Reference/SMTP_API/)が利用できます。以下の内容はメールヘッダに追加されます:


<h4>カテゴリヘッダの例</h4>

{% codeblock lang:json %}
{
  "category": "Example Category"
}
{% endcodeblock %}

この例では、SendGridはヘッダに**Example Category**というカテゴリを含むメールの統計情報と結びつけます。

1メッセージあたり最大10カテゴリまで割り当てることができます:

{% codeblock lang:json %}
{
  "category": [
    "dogs",
    "animals",
    "pets",
    "mammals"
  ]
}
{% endcodeblock %}
