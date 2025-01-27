---
order: 98
icon: log
label: Template
---

**Templates** in Kursaha are a powerful feature designed to streamline and enhance your communication strategies. They allow you to create, customize, and manage standardized content for various communication channels, including text-to-speech, email, push notifications, WhatsApp (both Interakt and standard), SMS, and OTPs. By leveraging templates, you ensure consistency in messaging, save time, and optimize your engagement efforts across different platforms.

## Benefits of Using Templates

- **Consistency Across Channels**: Templates ensure a uniform message across all communication channels, maintaining brand integrity and providing a cohesive user experience.

- **Time Efficiency**: Save time by reusing and adapting existing templates instead of creating new content from scratch for each campaign or interaction.

- **Enhanced Personalization**: Easily customize templates to address specific audience segments or individual preferences, improving engagement and relevance.

- **Streamlined Communication**: Simplify the process of creating and sending messages, reducing errors and ensuring timely delivery of communications.

- **Improved Brand Messaging**: Consistently present your brand’s voice and style across various platforms, enhancing brand recognition and trust.

- **Optimized Engagement**: Utilize well-designed templates to craft compelling messages that drive user actions, such as clicks, responses, or conversions.

By incorporating templates into your communication strategy, you streamline the process of crafting messages, maintain consistency, and enhance the effectiveness of your campaigns. Templates in Kursaha offer a flexible and efficient way to manage content across multiple channels, ensuring that your communications are both professional and impactful.

## How to Create a Template

Before creating a template, make sure that you have a valid datasource and query.

### Placeholder Format

When writing a template, it is important to use proper placeholders. The format for placeholders should be as follows: `[(${value})]`. Here, `value` is the query mapping name that you have given to build the query.
We use [Thymeleaf](https://www.thymeleaf.org/index.html) for mail templating. When creating a mail template, you need to:

1. Choose the type of template you want to create, such as text or HTML.
2. Write your template, and include placeholders where you want dynamic content to appear.

#### Sample with Default Value

Consider the following sample template:

```
Dear [(${name != null ? name : 'Valuable Customer'})],
Please find attached the results of the report you requested.

Sincerely,
Kursaha Tech.
```

In this template, we have used the `name` placeholder, and given it a default value of `Valuable Customer`. When you provide the JSON data `{'name': 'Josh'}`, the output will be:

```
Dear Josh,
Please find attached the results of the report you requested.

Sincerely,
Kursaha Tech.
```

By using proper placeholders, you can create dynamic templates that can be filled with data for multiple users.

#### Sample with Array Value

Suppose we have an array of names in our JSON data, like this:

```
{
    "names": ["John", "Jane", "Joe"]
}
```

We can use this array in our template like so:

```
Dear [(${name})],

Here are the names you requested:
<ul>
    <li th:each="name : ${names}">
        <span th:text="${name}"></span>
    </li>
</ul>

Sincerely,
Kursaha Tech.


JSON Data: {"name": "Josh", "names": ["John", "Jane", "Joe"]}

```

Output:

```
Dear Josh,

Here are the names you requested:
<ul>
    <li>John</li>
    <li>Jane</li>
    <li>Joe</li>
</ul>

Sincerely,
Kursaha Tech.

```

In the above example, we use Thymeleaf's th:each attribute to iterate over the names array and create an HTML list of names. We also include a placeholder for the name of the person we are addressing the email to `[(${name})]`. This placeholder will be replaced with the value of the name property in the JSON data.

## Our system supports these templates

- [Text To Speech](./TextToSpeech.md)
- [Mail](./Mail.md)
- [Push Notification](./PushNotification.md)
- [Whatsapp Interakt](./WhatsappInterakt.md)
- [Whatsapp](./Whatsapp.md)
- [SMS](./SMS.md)
- [OTP](./OTP.md)
