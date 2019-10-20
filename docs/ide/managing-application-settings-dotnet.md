---
title: Správa nastavení aplikace (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4215987ee0a61935efe27ab927d826cc1c6ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654621"
---
# <a name="manage-application-settings-net"></a>Správa nastavení aplikace (.NET)

Nastavení aplikace umožňují dynamicky ukládat informace o aplikaci. Nastavení umožňují ukládat informace v klientském počítači, které by neměly být zahrnuty do kódu aplikace (například připojovací řetězec), předvolby uživatele a další informace, které potřebujete v době běhu.

Nastavení aplikace nahradí dynamické vlastnosti používané v dřívějších verzích sady Visual Studio.

Každé nastavení aplikace musí mít jedinečný název. Název může být libovolná kombinace písmen, číslic nebo podtržítka, která nesmí začínat číslicí a nesmí obsahovat mezery. Název se změní prostřednictvím vlastnosti `Name`.

Nastavení aplikace lze uložit jako libovolný datový typ serializovaný do formátu XML nebo má `TypeConverter`, který implementuje `ToString` / `FromString`. Nejběžnější typy jsou `String`, `Integer` a `Boolean`, ale můžete také ukládat hodnoty jako <xref:System.Drawing.Color>, <xref:System.Object> nebo jako připojovací řetězec.

Nastavení aplikace také drží hodnotu. Hodnota je nastavena s vlastností **Value** a musí odpovídat datovému typu nastavení.

Kromě toho může být nastavení aplikace svázána s vlastností formuláře nebo ovládacího prvku v době návrhu.

Existují dva typy nastavení aplikace založené na rozsahu:

- Nastavení s rozsahem aplikace lze použít pro informace, jako je například adresa URL webové služby nebo databázového připojovacího řetězce. Tyto hodnoty jsou přidruženy k aplikaci. Proto je uživatelé nemohou měnit v době běhu.

- Nastavení s rozsahem uživatele lze použít pro informace, jako je například uchování poslední pozice formuláře nebo Předvolby písma. Uživatelé mohou tyto hodnoty v době běhu změnit.

Typ nastavení lze změnit pomocí vlastnosti **Scope** .

Systém projektu ukládá nastavení aplikace ve dvou souborech XML:

- soubor *App. config* , který je vytvořen v době návrhu při vytváření prvního nastavení aplikace

- soubor *User. config* , který je vytvořen v době běhu, když uživatel, který spouští aplikaci, změní hodnotu jakéhokoli nastavení uživatele.

Všimněte si, že změny v nastavení uživatele nejsou zapsány na disk, pokud aplikace konkrétně nevolá metodu, která to provede.

## <a name="create-application-settings-at-design-time"></a>Vytvoření nastavení aplikace v době návrhu

V době návrhu můžete vytvořit nastavení aplikace dvěma způsoby: pomocí stránky **Nastavení** **Návrháře projektu**nebo pomocí okna **vlastnosti** pro formulář nebo ovládací prvek, který umožňuje vytvořit svázání nastavení s vlastností.

Když vytvoříte nastavení s rozsahem aplikace (například připojovací řetězec databáze nebo odkaz na prostředky serveru), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ho uloží do *souboru App. config* se značkou `<applicationSettings>`. (Připojovací řetězce se ukládají pod značku `<connectionStrings>`.)

Když vytvoříte nastavení s rozsahem uživatele (například výchozí písmo, Domovská stránka nebo velikost okna), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ho uloží do *souboru App. config* se značkou `<userSettings>`.

> [!IMPORTANT]
> Když ukládáte připojovací řetězce do *souboru App. config*, měli byste podniknout opatření, abyste zabránili odhalení citlivých informací, jako jsou hesla nebo cesty na serveru, v připojovacím řetězci.
>
> Pokud převezmete informace připojovacího řetězce z externího zdroje, například uživatel, který zadal ID a heslo uživatele, musíte být opatrní, abyste zajistili, že hodnoty, které použijete k vytvoření připojovacího řetězce, neobsahují další parametry připojovacího řetězce. změny chování připojení.
>
> Zvažte použití funkce Protected Configuration k šifrování citlivých informací v konfiguračním souboru. Další informace najdete v tématu [ochrana informací o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Vzhledem k tomu, že není k dispozici žádný model konfiguračního souboru pro knihovny tříd, nastavení aplikace neplatí pro projekty knihovny tříd. Výjimkou je projekt Visual Studio Tools for Office DLL, který může mít konfigurační soubor.

## <a name="use-customized-settings-files"></a>Použít soubory s vlastním nastavením

Můžete přidat přizpůsobené soubory nastavení do projektu, abyste mohli pohodlně spravovat skupiny nastavení. Nastavení, která jsou obsažena v jednom souboru, jsou načtena a ukládána jako jednotka. Ukládání nastavení do samostatných souborů pro často používané a zřídka používané skupiny může ušetřit čas při načítání a ukládání nastavení.

Můžete například do svého projektu přidat soubor, například *SpecialSettings. Settings* . I když vaše třída `SpecialSettings` není vystavena v oboru názvů `My`, **zobrazení kódu** může přečíst soubor vlastního nastavení, který obsahuje `Partial Class SpecialSettings`.

**Návrhář nastavení** nejprve vyhledá soubor *Settings. Settings* , který vytváří systém projektu. Tento soubor je výchozím souborem, který **Návrhář projektu** zobrazuje na kartě **Nastavení** . *Settings. Settings* je umístěn ve složce *můj projekt* pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty a ve složce *Properties* for [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projects. **Návrhář projektu** pak vyhledá další soubory nastavení v kořenové složce projektu. Proto byste měli umístit soubor vlastních nastavení do souboru. Pokud přidáte soubor *. Settings* jinde v projektu, **Návrhář projektu** jej nebude moci vyhledat.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Přístup nebo změna nastavení aplikace za běhu v Visual Basic

V Visual Basic projekty můžete k nastavení aplikace přistupovat v době běhu pomocí objektu `My.Settings`. Na stránce **Nastavení** klikněte na tlačítko **Zobrazit kód** a zobrazte soubor *Settings. vb* . *Settings. vb* definuje třídu `Settings`, která umožňuje zpracovávat tyto události ve třídě nastavení: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Všimněte si, že třída `Settings` v *Settings. vb* je částečná třída, která zobrazuje pouze uživatelský kód, nikoli celou generovanou třídu. Další informace o přístupu k nastavení aplikace pomocí objektu `My.Settings` najdete v tématu [přístup k nastavení aplikace (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Hodnoty všech nastavení v uživatelském rozsahu, které uživatel změní v době běhu (například pozice formuláře), jsou uloženy v souboru *User. config* . Všimněte si, že výchozí hodnoty jsou pořád uložené v *App. config*.

Pokud se během běhu změní jakékoli nastavení s rozsahem uživatele, například při testování aplikace a chcete resetovat tato nastavení na výchozí hodnoty, klikněte na tlačítko **synchronizovat** .

Důrazně doporučujeme, abyste pro přístup k nastavení použili objekt `My.Settings` a soubor Default *. Settings* . Důvodem je, že můžete použít **Návrháře nastavení** k přiřazení vlastností nastavení, a navíc se uživatelská nastavení automaticky ukládají před vypnutím aplikace. Vaše aplikace Visual Basic však může získat přímý přístup k nastavení. V takovém případě musíte získat přístup ke třídě `MySettings` a použít vlastní soubor *. Settings* v kořenu projektu. Před ukončením aplikace je nutné uložit uživatelská nastavení, stejně jako v případě C# aplikace. Tento postup je popsaný v následující části.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Přístup nebo změna nastavení aplikace v době běhu vC#
<!-- markdownlint-enable MD003 MD020 -->

V jiných jazycích než Visual Basic, například C#, je nutné přistupovat přímo ke třídě `Settings`, jak je znázorněno v následujícím příkladu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Chcete-li zachovat nastavení uživatele, je nutné explicitně volat metodu `Save` této obálkové třídy. Obvykle to provedete v obslužné rutině události `Closing` hlavním formuláři. Následující C# příklad ukazuje volání metody `Save`.

```csharp
Properties.Settings.Default.Save();
```

Obecné informace o přístupu k nastavení aplikace prostřednictvím třídy `Settings` najdete v tématu [Přehled nastavení aplikace (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Informace o iteraci v nastaveních najdete v tomto [příspěvku na fóru](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Viz také:

- [Přístup k nastavení aplikace (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
