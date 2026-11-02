# Lab 01 — Packet Tracer introduction
# لاب 1 — مقدمة إلى Packet Tracer

[← All labs](../README.md) · [Download lab](./lab_file.pkt)

## Objective
## الهدف

Practise the Packet Tracer interface by placing, naming, and connecting devices in a simple two-branch topology.

التدرّب على واجهة Packet Tracer من خلال وضع الأجهزة وتسميتها وتوصيلها في رسم لشبكتين بفرعين مختلفين.

**Scope: topology construction and device identification. End-to-end IP connectivity and firewall protection have not been demonstrated in this documentation.**

**نطاق اللاب: بناء التوبولوجي وتمييز الأجهزة. هذا التوثيق لا يثبت نجاح الاتصال بين الطرفين أو عمل حماية الجدران النارية.**

## Files
## الملفات

| File | Purpose / الغرض |
| :--- | :--- |
| [lab_file.pkt](./lab_file.pkt) | Packet Tracer workspace / ملف العمل |
| [topology.png](./topology.png) | Saved topology preview / صورة التوبولوجي |
| README.md | Instructions and review checklist / التعليمات وقائمة المراجعة |

The Packet Tracer version used to save the workspace has not been recorded. Record your version when opening or reporting an issue.

إصدار Packet Tracer المستخدم لحفظ الملف غير مسجّل. سجّل إصدارك عند فتح الملف أو الإبلاغ عن مشكلة.

## Topology and device roles
## التوبولوجي ووظائف الأجهزة

| Location / الموقع | Devices / الأجهزة | Role / الوظيفة |
| :--- | :--- | :--- |
| New York | PC1, PC2; 2960-24TT SW1; 2911 R1; ASA 5505 FW1 | User devices, local switching, routing, firewall position / أجهزة المستخدمين والسويتش والتوجيه وموقع الجدار الناري |
| Transit | 2911 named “The Internet” | Simplified transit router / راوتر عبور مبسّط |
| Tokyo | SRV1, SRV2; 2960-24TT SW2; 2911 R2; ASA 5505 FW2 | Servers, local switching, routing, firewall position / السيرفرات والسويتش والتوجيه وموقع الجدار الناري |
| External segment | Laptop named ATTACKER | External-host placeholder / جهاز يمثل طرفاً خارجياً |

The inventory in the preview is 3 routers, 2 switches, 2 firewalls, 2 PCs, 2 servers, and 1 laptop.

الأجهزة الظاهرة بالصورة: 3 راوترات، وسويتشان، وجداران ناريان، وحاسوبان، وسيرفران، ولابتوب واحد.

“The Internet” is a label for a single simulated router, not a real Internet connection or a complete ISP network. The ATTACKER label alone does not simulate an attack.

اسم “The Internet” يمثّل راوتراً واحداً داخل المحاكاة، وليس اتصال إنترنت حقيقياً أو شبكة مزوّد خدمة كاملة. واسم ATTACKER وحده لا ينفّذ محاكاة هجوم.

## Topology preview
## صورة التوبولوجي

![Two-branch Packet Tracer topology with several red link indicators](./topology.png)

**The saved preview contains several red link indicators. It illustrates device placement and cabling, not a fully operational network.**

**الصورة المحفوظة فيها عدة مؤشرات وصلات حمراء. هي توضّح توزيع الأجهزة والتوصيلات، ولا تثبت أن الشبكة تعمل بالكامل.**

A green indicator does not prove end-to-end IP reachability. A red indicator requires checking the connected interfaces, cable, power, and administrative state; it does not identify the cause by itself.

المؤشر الأخضر لا يثبت نجاح الاتصال عبر الشبكة كاملة. المؤشر الأحمر يحتاج فحص الواجهات والكابل والطاقة وحالة تفعيل المنفذ؛ اللون وحده لا يحدّد السبب.

## Connections to inspect
## التوصيلات المطلوب فحصها

These are device-to-device connections visible in the preview. Exact port numbers and cable types must be inspected in the workspace; they are not readable in this screenshot.

هذه التوصيلات ظاهرة بين الأجهزة بالصورة. أرقام المنافذ وأنواع الكوابل الدقيقة لازم تُفحص داخل ملف العمل؛ مش مقروءة بهالصورة.

| Segment / الجزء | Device path / مسار الأجهزة |
| :--- | :--- |
| New York endpoints / أجهزة نيويورك | PC1 ↔ SW1; PC2 ↔ SW1 |
| New York uplink / ربط نيويورك | SW1 ↔ R1 ↔ FW1 ↔ The Internet |
| Tokyo uplink / ربط طوكيو | The Internet ↔ R2 ↔ FW2 ↔ SW2 |
| Tokyo endpoints / أجهزة طوكيو | SW2 ↔ SRV1; SW2 ↔ SRV2 |
| External host / الجهاز الخارجي | ATTACKER ↔ The Internet |

FW1 is outside R1 toward the transit segment; FW2 is inside R2 toward the server LAN. These placements illustrate two possible positions. Security depends on configuration and the traffic path.

FW1 موجود خارج R1 باتجاه شبكة العبور، وFW2 داخل R2 باتجاه شبكة السيرفرات. هذان مثالان لمواقع الجدار الناري؛ الأمان يعتمد على الإعدادات ومسار الحركة.

## Reproduce and inspect the lab
## خطوات إعادة البناء والفحص

1. Download and open `lab_file.pkt`. Save a separate copy before experimenting.

   نزّل الملف وافتحه، واحفظ نسخة منفصلة قبل التجربة.

2. Find the router, switch, firewall, PC, server, and laptop categories. Compare the models and device labels with the inventory.

   حدّد فئات الراوتر والسويتش والجدار الناري والحاسوب والسيرفر واللابتوب، وقارن الموديلات والأسماء مع الجدول.

3. Inspect each cable endpoint in Packet Tracer. Record both interface names and the cable type before deciding whether to change it.

   افحص طرفي كل كابل داخل البرنامج، وسجّل اسم الواجهة عند كل طرف ونوع الكابل قبل ما تقرّر تغيّره.

4. Check that all devices are powered on. Allow time for link initialization, then inspect any red links.

   تأكد أن الأجهزة تعمل، وانتظر تهيئة الوصلات، ثم افحص الوصلات الحمراء.

5. On IOS routers, use the read-only commands below to inspect interfaces.

   على راوترات IOS، استخدم أوامر العرض التالية لفحص الواجهات.

```text
enable
show ip interface brief
show interfaces
```

If an interface reports `administratively down`, it is administratively disabled. Enabling the intended interface with `no shutdown` may be needed in a configuration exercise, but that alone does not configure addressing, routing, or firewall policy.

إذا كانت الواجهة تعرض `administratively down` فهي معطّلة إدارياً. قد تحتاج تفعيل الواجهة المقصودة بأمر `no shutdown` في تمرين إعدادات، لكن هذا وحده لا يضبط العناوين أو التوجيه أو سياسة الجدار الناري.

ASA 5505 uses switch ports and VLAN interfaces. Do not assume it is configured exactly like a 2911 router.

ASA 5505 يستخدم منافذ سويتش وواجهات VLAN. لا تفترض أن طريقة إعداده مطابقة للراوتر 2911.

## Learning checks
## أسئلة الفهم

- **Why use SW1 and SW2?** To connect local endpoints.

  **ليش نستخدم السويتشين؟** لربط الأجهزة الطرفية محلياً.

- **Why use R1 and R2?** To route between different networks once configured.

  **ليش نستخدم الراوترين؟** لتوجيه الحركة بين الشبكات المختلفة بعد إعدادها.

- **Does placing FW1 and FW2 prove security?** No; interfaces and security policies must be configured and tested.

  **وجود الجدارين يثبت الأمان؟** لا؛ لازم إعداد الواجهات والسياسات واختبارها.

- **What is the intended PC1-to-SRV1 path?** PC1 → SW1 → R1 → FW1 → transit router → R2 → FW2 → SW2 → SRV1.

  **ما مسار PC1 إلى SRV1 المقصود؟** الحاسوب ثم سويتش الفرع ثم راوتره وجدار الحماية، وبعدها راوتر العبور، ثم راوتر طوكيو وجدار الحماية والسويتش والسيرفر. هذا مسار تصميمي، وليس نتيجة اختبار ناجح.

## Review checklist
## قائمة المراجعة

- [ ] Identify every device and explain its role.
      
      حدّد كل جهاز واشرح وظيفته.
- [ ] Compare workspace labels and connections with the saved preview.
      
      قارن أسماء الأجهزة والتوصيلات داخل الملف مع الصورة.
- [ ] Record connected interfaces and cable types from Packet Tracer.
      
      سجّل الواجهات المتصلة وأنواع الكوابل من البرنامج.
- [ ] Explain any red links using interface evidence rather than guessing.
      
      فسّر الوصلات الحمراء بناءً على حالة الواجهات بدل التخمين.
- [ ] Distinguish physical link status from IP reachability and security enforcement.
      
      ميّز بين حالة الوصلة، ونجاح اتصال IP، وتطبيق قواعد الأمان.

These are learner checks, not completed or automated test results. The binary workspace has not been executed as part of this documentation review.

هذه خطوات فحص للمتعلّم، وليست نتائج اختبارات مكتملة أو آلية. ملف العمل لم يُشغّل ضمن مراجعة هذا التوثيق.

## Further configuration
## إعدادات لاحقة

To turn this into a working connectivity lab, add an addressing plan, interface configuration, routing, ASA VLAN/interface and security settings, and recorded tests for allowed and denied traffic. Those tasks are beyond this introductory lab.

لتحويله إلى لاب اتصال فعلي، أضف خطة عناوين، وإعداد الواجهات والتوجيه وواجهات VLAN وسياسات ASA، وسجّل نتائج اختبارات الحركة المسموحة والممنوعة. هذه مهام لاحقة خارج نطاق اللاب التعريفي.

## References
## المراجع

- [Cisco IOS interface inspection](https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/cmdrefs/show_ip_interface.htm)
- [Cisco ASA 5505 ports and VLAN interfaces](https://www.cisco.com/c/en/us/td/docs/security/asa/asa92/configuration/general/asa-general-cli/interface-basic-5505.html)
