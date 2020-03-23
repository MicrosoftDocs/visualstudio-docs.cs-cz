---
title: Správa nastavení aplikace (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d792a6147795f81211203fc442539371f3caa91
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593704"
---
# <a name="manage-application-settings-net"></a>Správa nastavení aplikace (.NET)

Nastavení aplikace umožňuje dynamicky ukládat informace o aplikaci. Nastavení umožňují ukládat informace v klientském počítači, které by neměly být zahrnuty do kódu aplikace (například připojovací řetězec), uživatelské předvolby a další informace, které potřebujete za běhu.

Nastavení aplikace nahradit dynamické vlastnosti používané v dřívějších verzích sady Visual Studio.

Každé nastavení aplikace musí mít jedinečný název. Název může být libovolná kombinace písmen, čísel nebo podtržítka, která nezačíná číslem a nemůže obsahovat mezery. Název se změní `Name` prostřednictvím vlastnosti.

Nastavení aplikace lze uložit jako libovolný datový typ, který `TypeConverter` je `ToString` / `FromString`serializován do jazyka XML nebo má implementuje . Nejběžnější typy jsou `String` `Integer`, `Boolean`, a , ale <xref:System.Drawing.Color>můžete <xref:System.Object>také uložit hodnoty jako , nebo jako připojovací řetězec.

Nastavení aplikace také obsahuje hodnotu. Hodnota je nastavena s **Vlastností Value** a musí odpovídat datovému typu nastavení.

Kromě toho může být nastavení aplikace vázáno na vlastnost formuláře nebo ovládacího prvku v době návrhu.

Existují dva typy nastavení aplikací na základě oboru:

- Nastavení s rozsahem aplikace lze použít pro informace, jako je například adresa URL webové služby nebo připojovací řetězec databáze. Tyto hodnoty jsou přidruženy k aplikaci. Proto uživatelé nemohou změnit za běhu.

- Nastavení s uživatelským rozsahem lze použít pro informace, jako je například zachování poslední pozice formuláře nebo předvolby písma. Uživatelé mohou tyto hodnoty změnit za běhu.

Typ nastavení můžete změnit pomocí vlastnosti **Scope.**

Systém projektu ukládá nastavení aplikace do dvou souborů XML:

- soubor *app.config,* který je vytvořen v době návrhu při vytváření prvního nastavení aplikace

- soubor *user.config,* který je vytvořen za běhu, když uživatel, který aplikaci spouští, změní hodnotu libovolného uživatelského nastavení.

Všimněte si, že změny v nastavení uživatele nejsou zapsány na disk, pokud aplikace konkrétně volá metodu k tomu.

## <a name="create-application-settings-at-design-time"></a>Vytvoření nastavení aplikace v době návrhu

V době návrhu můžete vytvořit nastavení aplikace dvěma způsoby: pomocí stránky **Nastavení** **návrháře projektu**nebo pomocí okna **Vlastnosti** formuláře nebo ovládacího prvku, které umožňuje svázat nastavení s vlastností.

Když vytvoříte nastavení s rozsahem aplikace (například připojovací řetězec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] databáze nebo odkaz na prostředky `<applicationSettings>` serveru), uloží ho do *souboru app.config* se značkou. (Připojovací řetězce `<connectionStrings>` jsou uloženy pod značkou.)

Když vytvoříte nastavení s rozsahem uživatele (například výchozí písmo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] domovskou stránku nebo velikost `<userSettings>` okna), uloží ho do *souboru app.config* se značkou.

> [!IMPORTANT]
> Při ukládání připojovacích řetězců v *souboru app.config*byste měli přijmout opatření, aby se zabránilo odhalení citlivých informací, jako jsou hesla nebo cesty k serveru, v připojovacím řetězci.
>
> Pokud budete mít informace o připojovacím řetězci z externího zdroje, jako je například uživatel, který poskytuje ID uživatele a heslo, musíte být opatrní, abyste zajistili, že hodnoty, které použijete k vytvoření připojovacího řetězce, neobsahují další parametry připojovacího řetězce které mění chování připojení.
>
> Zvažte použití funkce Chráněná konfigurace k šifrování citlivých informací v konfiguračním souboru. Další informace naleznete v tématu [Ochrana informací o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Vzhledem k tomu, že neexistuje žádný model konfiguračního souboru pro knihovny tříd, nastavení aplikace se nevztahuje na projekty knihovny tříd. Výjimkou je projekt DLL sady Visual Studio Tools for Office, který může mít konfigurační soubor.

## <a name="use-customized-settings-files"></a>Použití souborů přizpůsobených nastavení

Do projektu můžete přidat soubory přizpůsobených nastavení pro pohodlnou správu skupin nastavení. Nastavení obsažená v jednom souboru jsou načtena a uložena jako celek. Ukládání nastavení do samostatných souborů pro často používané a zřídka používané skupiny může ušetřit čas při načítání a ukládání nastavení.

Do projektu můžete například přidat soubor, například *SpecialSettings.settings.* Zatímco `SpecialSettings` vaše třída není `My` vystavena v oboru názvů, **zobrazit** kód `Partial Class SpecialSettings`můžete číst vlastní nastavení souboru, který obsahuje .

**Návrhář nastavení** nejprve vyhledá soubor *Settings.settings,* který vytvoří systém projektu. tento soubor je výchozí soubor, který **návrhář** projektu *Settings.settings* zobrazuje na kartě *My Project* [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] **Nastavení.** *Properties* [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] **Návrhář projektu** pak vyhledá další soubory nastavení v kořenové složce projektu. Proto byste měli umístit vlastní soubor nastavení tam. Pokud přidáte soubor *nastavení* jinde v projektu, **Návrhář projektu** jej nebude moci najít.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Přístup k nastavení aplikace nebo změna nastavení aplikace za běhu v jazyce Visual Basic

V projektech jazyka Visual Basic můžete přistupovat `My.Settings` k nastavení aplikace za běhu pomocí objektu. Na stránce **Nastavení** klikněte na tlačítko **Zobrazit kód** a zobrazte soubor *Settings.vb.* *Soubor Settings.vb* `Settings` definuje třídu, která umožňuje zpracovávat tyto <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>události <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>třídě nastavení: , , , a . Všimněte `Settings` si, že třída v *Settings.vb* je částečná třída, která zobrazuje pouze kód vlastněný uživatelem, nikoli celou vygenerovanou třídu. Další informace o přístupu k `My.Settings` nastavení aplikace pomocí objektu naleznete v tématu [Nastavení aplikace Access (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Hodnoty všech nastavení s rozsahem uživatele, které uživatel změní za běhu (například pozice formuláře), jsou uloženy v souboru *user.config.* Všimněte si, že výchozí hodnoty jsou stále uloženy v *souboru app.config*.

Pokud se za běhu změní nastavení s rozsahem uživatele, například při testování aplikace, a chcete tato nastavení obnovit na výchozí hodnoty, klepněte na tlačítko **Synchronizovat.**

Důrazně doporučujeme použít `My.Settings` objekt a výchozí soubor *nastavení* pro přístup k nastavení. Je to proto, **že můžete** použít Návrhář nastavení přiřadit vlastnosti k nastavení a navíc uživatelská nastavení jsou automaticky uloženy před vypnutím aplikace. Aplikace jazyka Visual Basic však může přistupovat k nastavení přímo. V takovém případě budete `MySettings` mít přístup ke třídě a použít vlastní soubor *.settings* v kořenovém adresáři projektu. Před ukončením aplikace je nutné uložit nastavení uživatele, stejně jako pro aplikaci jazyka C#. to je popsáno v následující části.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Přístup nebo změna nastavení aplikace za běhu v C #
<!-- markdownlint-enable MD003 MD020 -->

V jiných jazycích než Visual Basic, jako `Settings` je například C#, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] musíte přistupovat ke třídě přímo, jak je znázorněno v následujícím příkladu.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Je nutné explicitně volat `Save` metodu této třídy obálky, aby bylo zachováno uživatelské nastavení. Obvykle to uděláte `Closing` v obslužné rutině události hlavního formuláře. Následující příklad Jazyka C# ukazuje `Save` volání metody.

```csharp
Properties.Settings.Default.Save();
```

Obecné informace o přístupu k `Settings` nastavení aplikace prostřednictvím třídy naleznete v tématu [Přehled nastavení aplikace (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Informace o iterace prostřednictvím nastavení naleznete v tomto [příspěvku na fóru](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Viz také

- [Přístup k nastavení aplikace (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
