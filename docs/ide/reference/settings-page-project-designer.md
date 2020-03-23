---
title: Stránka Nastavení, Návrhář projektu
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4ca1def334241999445e3f11cf142aa426d962
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566771"
---
# <a name="settings-page-project-designer"></a>Stránka Nastavení, Návrhář projektu

Na stránce **Nastavení** Návrháře projektu můžete určit nastavení aplikace projektu. Nastavení aplikace umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Umožňují také udržovat vlastní předvolby aplikací a uživatelů v klientském počítači. Další informace naleznete v [tématu Správa nastavení aplikace](../managing-application-settings-dotnet.md).

Chcete-li získat přístup ke stránce **Nastavení,** vyberte uzel projektu v **Průzkumníku řešení**a pak vyberte**Vlastnosti** **projektu** > . Po zobrazení Návrháře projektů vyberte kartu **Nastavení.**

## <a name="header-bar"></a>Záhlaví

Záhlaví v horní části stránky **Nastavení** obsahuje několik ovládacích prvků:

**Synchronizovat**

**Synchronizace** obnoví nastavení s rozsahem uživatele, které aplikace používá za běhu nebo během ladění na výchozí hodnoty, jak je definováno v době návrhu. Chcete-li obnovit data, odeberte soubory specifické pro aplikaci generované za běhu z disku, nikoli z dat projektu.

**Načíst nastavení webu**

**Načíst nastavení webu** se zobrazí dialogové okno **Přihlášení,** které umožňuje načíst nastavení pro ověřeného uživatele nebo pro anonymní uživatele. Toto tlačítko je povoleno pouze v případě, že jste povolili služby klientských aplikací na stránce **Služby** a zadali **umístění služby Nastavení webu**.

**Zobrazit kód**

Pro projekty jazyka C# **tlačítko Zobrazit kód** umožňuje zobrazit kód v *souboru Settings.cs.* Tento soubor definuje `Settings` třídu, která umožňuje zpracovávat `Settings` určité události na objektu. V jiných jazycích než visual basic, je nutné explicitně volat `Save` metodu této obálky třídy, aby se zachovat nastavení uživatele. Obvykle to uzavřete v obslužné rutině události **Closing** hlavního formuláře. Následuje příklad volání `Save` metody:

```csharp
Properties.Settings.Default.Save();
```

U projektů jazyka Visual Basic umožňuje tlačítko **Zobrazit kód** zobrazit kód v souboru *Settings.vb.* Tento soubor definuje `MySettings` třídu, která umožňuje zpracovávat `My.Settings` určité události na objektu. Další informace o přístupu k `My.Settings` nastavení aplikace pomocí objektu naleznete v tématu [Nastavení aplikace Access](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Další informace o přístupu k nastavení aplikace naleznete v [tématu Nastavení aplikací pro windows forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modifikátor přístupu**

Tlačítko **Modifikátor přístupu** určuje `Properties.Settings` úroveň přístupu (v jazyce C#) nebo `My.Settings` (v jazyce Visual Basic), které sada Visual Studio generuje v *Settings.Designer.cs* nebo *Settings.Designer.vb*.

Pro projekty Visual C# modifikátor přístupu může být **Interní** nebo **Public**.

U projektů jazyka Visual Basic může být modifikátor **přístupu Friend** nebo **Public**.

Ve výchozím nastavení je nastavení **Interní** v jazyce C# a **Friend** v jazyce Visual Basic. Když Visual Studio generuje pomocné třídy jako **interní** nebo **friend**, spustitelné aplikace *(.exe)* aplikace nemají přístup k prostředkům a nastavení, které jste přidali do knihoven tříd *(dll* soubory). Pokud máte sdílet prostředky a nastavení z knihovny tříd, nastavte modifikátor přístupu na **Veřejné**.

Další informace o třídách pomocníka nastavení naleznete v [tématu Správa nastavení aplikace](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Mřížka nastavení

**Nastavení mřížky** se používá ke konfiguraci nastavení aplikace. Tato mřížka obsahuje následující sloupce:

**Název**

Do tohoto pole zadejte název nastavení aplikace.

**Typ**

Pomocí rozevíracího seznamu vyberte typ nastavení. Nejčastěji používané typy se zobrazí v rozevíracím seznamu, například **Řetězec** **( připojovací řetězec)** a **System.Drawing.Font**. Jiný typ můžete zvolit tak, že **vyberete Procházet** na konci seznamu a pak vyberete typ z dialogového okna **Vybrat typ.** Po výběru typu se přidá do běžných typů v rozevíracím seznamu (pouze pro aktuální řešení).

**Rozsah**

Vyberte **aplikaci** nebo **uživatele**.

Nastavení s rozsahem aplikace, jako jsou například připojovací řetězce, jsou přidruženy k aplikaci. Uživatelé nemohou měnit nastavení s rozsahem aplikace za běhu.

Nastavení s uživatelským rozsahem, například systémová písma, jsou určena pro použití pro uživatelské předvolby. Uživatelé je mohou měnit za běhu.

**Hodnotu**

Data nebo hodnota přidružená k nastavení aplikace. Pokud je například nastavenípísmo, může být jeho hodnota **Verdana, 9,75 bodů, style=Tučné**.

## <a name="see-also"></a>Viz také

- [Správa nastavení aplikace](../managing-application-settings-dotnet.md)
- [Přístup k nastavení aplikace (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
