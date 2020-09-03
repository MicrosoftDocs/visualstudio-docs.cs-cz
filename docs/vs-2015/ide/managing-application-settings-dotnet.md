---
title: Správa nastavení aplikace (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85cc90170b2dc665bcdd5acd97860c47ef5a14c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293864"
---
# <a name="managing-application-settings-net"></a>Správa nastavení aplikace (.NET)

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení aplikace umožňují dynamicky ukládat informace o aplikaci. Nastavení umožňují ukládat informace na klientském počítači, které by neměly být zahrnuty do kódu aplikace (například připojovací řetězec), uživatelských předvoleb a dalších informací, které potřebujete za běhu.

Nastavení aplikace nahradí dynamické vlastnosti používané v dřívějších verzích sady Visual Studio.

Každé nastavení aplikace musí mít jedinečný název. Název může být libovolná kombinace písmen, číslic nebo podtržítka, která nesmí začínat číslicí a nesmí obsahovat mezery. Název lze změnit pomocí `Name` Vlastnosti.

Nastavení aplikace lze uložit jako libovolný datový typ, který lze serializovat do formátu XML nebo který má `TypeConverter` implementováno `ToString` / `FromString` . Nejběžnější typy jsou `String` , a, `Integer` `Boolean` ale můžete také uložit hodnoty jako <xref:System.Drawing.Color> , <xref:System.Object> nebo jako připojovací řetězec.

Nastavení aplikace také obsahuje hodnotu. Hodnota je nastavena s vlastností **Value** a musí odpovídat datovému typu nastavení.

Kromě toho může být nastavení aplikace svázána s vlastností formuláře nebo ovládacího prvku v době návrhu.

Existují dva typy nastavení aplikace založené na rozsahu:

- Nastavení s rozsahem aplikace lze použít pro informace, jako je například adresa URL webové služby nebo databázového připojovacího řetězce. Tyto hodnoty jsou přidruženy k aplikaci. Proto je uživatelé nemohou měnit v době běhu.

- Nastavení s rozsahem uživatele lze použít pro informace, jako je například uchování poslední pozice formuláře nebo Předvolby písma. Uživatelé mohou tyto hodnoty v době běhu změnit.

  Typ nastavení lze změnit pomocí vlastnosti **Scope** .

  Systém projektu ukládá nastavení aplikace ve dvou souborech XML: app.config soubor, který je vytvořen v době návrhu při vytváření prvního nastavení aplikace. a user.config soubor, který je vytvořen v době běhu, když uživatel, který spouští aplikaci, změní hodnotu libovolného nastavení uživatele. Všimněte si, že změny v nastavení uživatele nejsou zapsány na disk, pokud aplikace konkrétně nevolá metodu, která to provede.

## <a name="creating-application-settings-at-design-time"></a>Vytváření nastavení aplikace v době návrhu

V době návrhu můžete vytvořit nastavení aplikace dvěma způsoby: pomocí stránky **Nastavení** **Návrháře projektu**nebo pomocí okna **vlastnosti** pro formulář nebo ovládací prvek, který umožňuje vytvořit svázání nastavení s vlastností.

Když vytvoříte nastavení s rozsahem aplikace (například připojovací řetězec databáze nebo odkaz na prostředky serveru), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uloží se do app.config se `<applicationSettings>` značkou. (Připojovací řetězce jsou uloženy pod `<connectionStrings>` značkou.)

Když vytvoříte nastavení s rozsahem uživatele (například výchozí písmo, Domovská stránka nebo velikost okna), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uloží se do app.config se `<userSettings>` značkou.

> [!IMPORTANT]
> Když ukládáte připojovací řetězce v app.config, měli byste podniknout opatření, abyste se vyhnuli odhalení citlivých informací, jako jsou hesla nebo cesty na serveru, v připojovacím řetězci.
>
> Pokud převezmete informace připojovacího řetězce z externího zdroje, například uživatel, který zadal ID a heslo uživatele, musíte být opatrní, abyste zajistili, že hodnoty, které použijete k vytvoření připojovacího řetězce, neobsahují další parametry připojovacího řetězce, které mění chování připojení.
>
> Zvažte použití funkce Protected Configuration k šifrování citlivých informací v konfiguračním souboru. Další informace najdete v tématu [ochrana informací o připojení](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) .

> [!NOTE]
> Vzhledem k tomu, že není k dispozici žádný model konfiguračního souboru pro knihovny tříd, nastavení aplikace neplatí pro projekty knihovny tříd. Výjimkou je projekt Visual Studio Tools for Office DLL, který může mít konfigurační soubor.

## <a name="using-customized-settings-files"></a>Použití souborů s vlastním nastavením

Můžete přidat přizpůsobené soubory nastavení do projektu, abyste mohli pohodlně spravovat skupiny nastavení. Nastavení, která jsou obsažena v jednom souboru, jsou načtena a ukládána jako jednotka. Proto schopnost ukládat nastavení v samostatných souborech pro často používané a zřídka používané skupiny může ušetřit čas při načítání a ukládání nastavení.

Můžete například do svého projektu přidat soubor, například SpecialSettings. Settings. I když vaše `SpecialSettings` třída není vystavena v `My` oboru názvů, **Zobrazit kód** může přečíst soubor vlastního nastavení, který `Partial Class SpecialSettings` obsahuje.

Návrhář nastavení nejprve vyhledá soubor Settings. Settings, který vytváří systém projektu. Toto je výchozí soubor, který návrhář projektu zobrazí na kartě **Nastavení** . Settings. Settings je umístěn ve složce můj projekt pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty a ve složce Properties (vlastnosti) pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty. Návrhář projektu pak vyhledá další soubory nastavení v kořenové složce projektu. Proto byste měli umístit soubor vlastních nastavení do souboru. Pokud přidáte soubor. Settings jinde v projektu, Návrhář projektu jej nebude moci vyhledat.

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Přístup k nastavení aplikace nebo jejich změna v době běhu v Visual Basic

V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektech můžete k nastavení aplikace přistupovat v době běhu pomocí `My.Settings` objektu. Na stránce **Nastavení** klikněte na tlačítko **Zobrazit kód** a zobrazte soubor Settings. vb. Settings. vb definuje `Settings` třídu, která umožňuje zpracovávat tyto události ve třídě nastavení: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> , <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . Všimněte si, že `Settings` Třída v Settings. vb je částečná třída, která zobrazuje pouze uživatelský kód, nikoli celou generovanou třídu. Další informace o přístupu k nastavení aplikace pomocí objektu najdete `My.Settings` v tématu věnovaném [přístupu k nastavení aplikace](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).

Hodnoty všech nastavení v uživatelském rozsahu, které uživatel změní v době běhu (například pozice formuláře), jsou uloženy v souboru user.config. Všimněte si, že výchozí hodnoty jsou pořád uložené v app.config.

Pokud jste v době běhu změnili nastavení s rozsahem uživatele, například při testování aplikace a chcete resetovat tato nastavení na výchozí hodnoty, klikněte na tlačítko **synchronizovat** .

Důrazně doporučujeme, abyste k `My.Settings` nastavení přístupu použili objekt a soubor default. Settings. Důvodem je, že můžete použít návrháře nastavení k přiřazení vlastností nastavení, a navíc se uživatelská nastavení automaticky ukládají před vypnutím aplikace. Vaše aplikace ale [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] může získat přímý přístup k nastavení. V takovém případě musíte získat přístup ke `MySettings` třídě a použít vlastní soubor. Settings v kořenu projektu. Před ukončením aplikace je také nutné uložit uživatelská nastavení, stejně jako v případě aplikace v jazyce C#. Tento postup je popsaný v následující části.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Přístup k nastavení aplikace nebo jejich změna v době běhu v jazyce Visual C #
<!-- markdownlint-enable MD003 MD020 -->

V jiných jazycích, jako je například [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] , je nutné přistupovat ke `Settings` třídě přímo, jak je znázorněno v následujícím [!INCLUDE[csprcs](../includes/csprcs-md.md)] příkladu.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Je také nutné explicitně volat `Save` metodu této obálkové třídy, aby bylo možné zachovat uživatelská nastavení. Obvykle to provedete v `Closing` obslužné rutině události v hlavním formuláři. Následující [!INCLUDE[csprcs](../includes/csprcs-md.md)] příklad ukazuje volání `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Obecné informace o přístupu k nastavení aplikace přes `Settings` třídu najdete v tématu [Přehled nastavení aplikace](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Informace o iteraci v nastaveních najdete v tomto [příspěvku na fóru](https://social.msdn.microsoft.com/Forums/en-US/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Viz také

- [Přístup k nastavení aplikace](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
