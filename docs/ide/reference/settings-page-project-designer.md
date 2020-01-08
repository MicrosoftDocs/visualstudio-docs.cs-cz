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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566771"
---
# <a name="settings-page-project-designer"></a>Stránka nastavení, Návrhář projektu

Stránku **Nastavení** Návrháře projektu použijte k určení nastavení aplikace projektu. Nastavení aplikace umožňují dynamicky ukládat a načítat nastavení vlastností a další informace pro aplikaci. Také umožňují udržovat vlastní aplikace a uživatelské předvolby v klientském počítači. Další informace najdete v tématu [Správa nastavení aplikace](../managing-application-settings-dotnet.md).

Pro přístup na stránku **Nastavení** vyberte uzel projektu v **Průzkumník řešení**a pak vyberte **vlastnosti** **projektu** > . Když se zobrazí Návrhář projektu, vyberte kartu **Nastavení** .

## <a name="header-bar"></a>Záhlaví

Záhlaví v horní části stránky **Nastavení** obsahuje několik ovládacích prvků:

**Synchronize**

**Synchronizace** obnoví nastavení s rozsahem uživatele, které aplikace používá v době běhu nebo během ladění na jejich výchozí hodnoty, jak je definováno v době návrhu. Chcete-li obnovit data, odstraňte soubory aplikace, které byly vytvořeny za běhu z disku, nikoli z dat projektu.

**Načíst nastavení webu**

**Možnost načíst webové nastavení** zobrazí dialogové okno **přihlášení** , které umožňuje načíst nastavení pro ověřeného uživatele nebo pro anonymní uživatele. Toto tlačítko je povoleno pouze v případě, že jste povolili klientské aplikační služby na stránce **služby** a zadali jste **umístění služby nastavení webu**.

**Zobrazit kód**

V C# případě projektů umožňuje tlačítko **Zobrazit kód** zobrazit kód v souboru *Settings.cs* . Tento soubor definuje třídu `Settings`, která umožňuje zpracovávat konkrétní události v objektu `Settings`. V jiných jazycích než Visual Basic je nutné explicitně volat metodu `Save` této obálkové třídy, aby bylo možné zachovat nastavení uživatele. Obvykle to provedete v obslužné rutině události **zavírání** hlavního formuláře. Následuje příklad volání metody `Save`:

```csharp
Properties.Settings.Default.Save();
```

U Visual Basic projektů umožňuje tlačítko **Zobrazit kód** zobrazit kód v souboru *Settings. vb* . Tento soubor definuje třídu `MySettings`, která umožňuje zpracovávat konkrétní události v objektu `My.Settings`. Další informace o přístupu k nastavení aplikace pomocí objektu `My.Settings` najdete v tématu [přístup k nastavení aplikace](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Další informace o přístupu k nastavení aplikace najdete v tématu [nastavení aplikace pro model Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modifikátor přístupu**

Tlačítko **modifikátoru přístupu** určuje úroveň přístupu `Properties.Settings` (in C#) nebo `My.Settings` (v Visual Basic) pomocných tříd, které Visual Studio generuje v *Settings.Designer.cs* nebo *Settings. Designer. vb*.

V případě C# vizuálních projektů může být modifikátor přístupu **interní** nebo **veřejný**.

U Visual Basic projektů může být modifikátor přístupu **přítel** nebo **veřejný**.

Ve výchozím nastavení je nastavení **interní** v C# a **příteli** v Visual Basic. Když aplikace Visual Studio vygeneruje pomocné třídy jako **interní** nebo **přítel**, spustitelné aplikace ( *. exe*) nemají přístup k prostředkům a nastavením, které jste přidali do knihoven tříd (soubory *. dll* ). Pokud potřebujete sdílet prostředky a nastavení z knihovny tříd, nastavte modifikátor přístupu na **veřejné**.

Další informace o pomocných třídách nastavení najdete v tématu [Správa nastavení aplikace](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Mřížka nastavení

Pro konfiguraci nastavení aplikace se používá **Mřížka nastavení** . Tato mřížka obsahuje následující sloupce:

**Jméno**

Do tohoto pole zadejte název nastavení aplikace.

**Typ**

Pomocí rozevíracího seznamu vyberte typ nastavení. Nejčastěji používané typy se zobrazí v rozevíracím seznamu, například **řetězec**, **(připojovací řetězec)** a **System. Drawing. Font**. Můžete zvolit jiný typ výběrem možnosti **Procházet** na konci seznamu a následným výběrem typu v dialogovém okně **Vybrat typ** . Po zvolení typu se tento typ přidá do společných typů v rozevíracím seznamu (pouze pro aktuální řešení).

**Rozsah**

Vyberte možnost **aplikace** nebo **uživatel**.

Nastavení s rozsahem aplikace, například připojovací řetězce, jsou přidružena k aplikaci. Uživatelé nemůžou v době běhu měnit nastavení v rozsahu aplikace.

Nastavení s rozsahem uživatele, jako jsou například systémová písma, je určeno k použití v uživatelských preferencích. Uživatelé je mohou měnit v době běhu.

**Hodnota**

Data nebo hodnota přidružená k nastavení aplikace. Pokud je například nastavení Font, může být jeho hodnota **Verdana, 9.75 PT, Style = Bold**.

## <a name="see-also"></a>Viz také:

- [Spravovat nastavení aplikace](../managing-application-settings-dotnet.md)
- [Přístup k nastavení aplikace (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
