---
title: Stránka Nastavení, Návrhář projektu
ms.date: 06/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c0f7b47b56522f5c4aeef0054e6b7b52434ff87
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "35608944"
---
# <a name="settings-page-project-designer"></a>Stránka nastavení, Návrhář projektu

Použití **nastavení** stránky Návrháře projektu k určení nastavení aplikace projektu. Nastavení aplikace umožňují snadno ukládat a načítat nastavení vlastností a další informace o vaší aplikaci dynamicky. Umožňují také udržovat vlastní aplikace a preference uživatelů v klientském počítači. Další informace najdete v tématu [spravovat nastavení aplikace](../managing-application-settings-dotnet.md).

Pro přístup **nastavení** stránky, vyberte uzel projektu v **Průzkumníka řešení**a pak vyberte **projektu** > **vlastnosti**. Jakmile se zobrazí Návrhář projektu, vyberte **nastavení** kartu.

## <a name="header-bar"></a>Záhlaví řádku

Na panelu záhlaví v horní části **nastavení** stránka obsahuje několik ovládacích prvků:

**Synchronizovat**

**Synchronizovat** obnoví nastavení rozsahu uživatele, které aplikace používá za běhu nebo při ladění na výchozí hodnoty, jak je definováno v době návrhu. Chcete-li obnovit data, odeberte za běhu generované soubory specifické pro aplikaci z disku, nikoli z dat projektu.

**Načtení webové nastavení**

**Načíst nastavení webu** zobrazí **přihlášení** dialogové okno, které umožňuje načíst nastavení pro ověřeného uživatele nebo pro anonymní uživatele. Toto tlačítko je povoleno pouze v případě, že jste povolili klientské aplikační služby na **služby** stránce a zadat **nastavení webové služby umístění**.

**Zobrazit kód**

Pro projekty jazyka C# **zobrazit kód** tlačítko umožňuje zobrazit kód v *Settings.cs* souboru. Tento soubor definuje `Settings` třídu, která umožňuje zpracovávat specifické události na `Settings` objektu. V jiných jazycích než jazyka Visual Basic, musíte explicitně volat `Save` metoda této obálkové třídy s cílem zachovat nastavení uživatele. Obvykle to provedete **zavření** obslužná rutina události hlavního formuláře. Tady je příklad volání `Save` metody:

```csharp
Properties.Settings.Default.Save();
```

Pro projekty jazyka Visual Basic **zobrazit kód** tlačítko umožňuje zobrazit kód v *Settings.vb* souboru. Tento soubor definuje `MySettings` třídu, která umožňuje zpracovávat specifické události na `My.Settings` objektu. Další informace o přístup k nastavení aplikace s použitím `My.Settings` objektu, najdete v článku [přístup k nastavení aplikace](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Další informace o přístupu k nastavení aplikace najdete v tématu [nastavení aplikace pro Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modifikátor přístupu**

**Modifikátor přístupu** tlačítko určuje úroveň přístupu `Properties.Settings` (v jazyce C#) nebo `My.Settings` (v jazyce Visual Basic) pomocné třídy, který generuje sada Visual Studio v *Settings.Designer.cs* nebo *Settings.Designer.vb*.

Pro projekty Visual C#, může být modifikátor přístupu **interní** nebo **veřejné**.

Pro projekty jazyka Visual Basic modifikátor přístupu lze **Friend** nebo **veřejné**.

Ve výchozím nastavení je **interní** v jazyce C# a **Friend** v jazyce Visual Basic. Když sada Visual Studio generuje pomocné třídy jako **interní** nebo **Friend**, spustitelný soubor (*.exe*) aplikace nemají přístup k prostředkům a nastavení, které jste přidali do třídy knihovny (*.dll* soubory). Pokud máte sdílet prostředky a nastavení z knihovny tříd, nastavit modifikátor přístupu **veřejné**.

Další informace o nastavení tříd pomocných rutin najdete v tématu [spravovat nastavení aplikace](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Nastavení mřížky

**Nastavení mřížky** slouží ke konfiguraci nastavení aplikace. Tato mřížka obsahuje následující sloupce:

**Jméno**

Zadejte název nastavení aplikace v tomto poli.

**Typ**

Pomocí rozevíracího seznamu vyberte typ nastavení. Nejčastěji používané typy v seznamu se zobrazí rozevírací seznam, například **řetězec**, **(připojovací řetězec)**, a **System.Drawing.Font**. Můžete tak, že vyberete jiný typ **Procházet** na konci seznamu a následným výběrem určitého typu **vyberte typ** dialogové okno. Až zvolíte typ, přidá se do běžných typů v rozevíracím seznamu (pro aktuální řešení pouze).

**Rozsah**

Vyberte buď **aplikace** nebo **uživatele**.

Nastavení oboru aplikace, jako je například připojovací řetězce, jsou spojeny s aplikací. Uživatelé nemohou změnit nastavení oboru aplikace v době běhu.

Nastavení rozsahu uživatele, jako je například systémových písem, jsou určena pro použití pro uživatelské předvolby. Uživatelé mohou změnit je za běhu.

**Hodnota**

Data nebo hodnotu přidruženou k nastavení aplikace. Například pokud je nastavení písma, jeho hodnota může být **Verdana 9.75pt, styl = tučné**.

## <a name="see-also"></a>Viz také:

- [Správa nastavení aplikace](../managing-application-settings-dotnet.md)
- [Přístup k nastavení aplikace (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)