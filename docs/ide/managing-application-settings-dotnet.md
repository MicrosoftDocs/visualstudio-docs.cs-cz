---
title: Správa nastavení aplikace (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4ea61199159e68f3707b6dac4d3a6c1f5ea7635
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671784"
---
# <a name="manage-application-settings-net"></a>Správa nastavení aplikace (.NET)

Nastavení aplikace umožňují uložení informací aplikace dynamicky. Nastavení vám umožňují ukládat informace na klientský počítač, který by neměl být zařazen do kódu aplikace (například připojovací řetězec), uživatelských předvoleb a dalších informací, které potřebujete v době běhu.

Nastavení aplikace nahradí dynamické vlastnosti použité v dřívějších verzích sady Visual Studio.

Každé nastavení aplikace musí mít jedinečný název. Název může obsahovat libovolnou kombinaci písmen, čísel nebo podtržítek, která nezačíná řetězcem číslo a nemůže obsahovat mezery. Název změnit prostřednictvím `Name` vlastnost.

Nastavení aplikace mohou být uloženy jako libovolného datového typu, který je serializován do formátu XML nebo má `TypeConverter` , který implementuje `ToString` / `FromString`. Nejběžnější typy jsou `String`, `Integer`, a `Boolean`, ale můžete také uložit hodnoty jako <xref:System.Drawing.Color>, <xref:System.Object>, nebo jako připojovací řetězec.

Nastavení aplikace také obsahovat hodnotu. Tato hodnota nastavená s **hodnotu** vlastnost a musí odpovídat datovému typu nastavení.

Kromě toho nastavení aplikace mohou být vázány na vlastnost formuláře nebo ovládacího prvku v době návrhu.

Existují dva typy nastavení aplikace založené na rozsahu:

- Nastavení oboru aplikace lze použít pro informace, jako je adresa URL pro webovou službu nebo připojovací řetězec databáze. Tyto hodnoty jsou spojeny s aplikací. Proto je uživatelé nemohou změnit za běhu.

- Nastavení s rozsahem uživatele lze použít pro informace, jako jsou například uchování poslední pozice formuláře nebo předvoleb písma. Uživatelé mohou změnit tyto hodnoty v době běhu.

Typ nastavení můžete změnit pomocí **oboru** vlastnost.

Systém projektu ukládá nastavení aplikace ve dvou souborech XML:

- *app.config* soubor, který je vytvořen v době návrhu, když vytvoříte první nastavení aplikace

- *user.config* soubor, který je vytvořen v době běhu, když uživatel, který spouští aplikaci změní hodnotu nastavení některého uživatele.

Všimněte si, že změny v nastavení uživatele nejsou zapsány na disk, pokud aplikace konkrétně nevolá metodu, chcete-li to provést.

## <a name="create-application-settings-at-design-time"></a>Vytvořit nastavení aplikace v době návrhu

V době návrhu, můžete vytvořit nastavení aplikace dvěma způsoby: pomocí **nastavení** stránku **Návrháře projektu**, nebo pomocí **vlastnosti** okna pro formulář nebo ovládací prvek, který umožňuje svázat nastavení vlastnosti.

Když vytvoříte nastavení s rozsahem aplikace (například připojovací řetězec databáze nebo odkaz na prostředky serveru), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uloží ho v *app.config* s `<applicationSettings>` značky. (Připojovací řetězce jsou uloženy v rámci `<connectionStrings>` značka.)

Když vytvoříte nastavení s rozsahem uživatele (například výchozí písmo, domovská stránka nebo velikost okna), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uloží ho v *app.config* s `<userSettings>` značky.

> [!IMPORTANT]
> Při ukládání připojovacích řetězců v *app.config*, byste měli podniknout opatření k zamezení odhalení citlivých informací, jako jsou hesla nebo cesty k serveru, v připojovacím řetězci.
>
> Pokud budete postupovat informace o připojovacím řetězci z externího zdroje, jako je například uživatelské zadání ID uživatele a heslo, musíte být opatrní a zkontrolujte, že hodnoty, které můžete použít k vytvoření připojení řetězec neobsahují další parametry připojovacího řetězce která mění chování vašeho připojení.
>
> Zvažte použití funkce Protected Configuration pro šifrování citlivých informací v konfiguračním souboru. Další informace najdete v tématu [chránit informace o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Protože neexistuje žádný model konfiguračního souboru pro knihovny tříd, nastavení aplikace nelze aplikovat na projekty knihovny tříd. Výjimkou je Visual Studio Tools for Office DLL projekt, který může mít konfigurační soubor.

## <a name="use-customized-settings-files"></a>Použití vlastních souborů nastavení

Soubory vlastního nastavení můžete přidat do projektu pro pohodlné řízení skupin nastavení. Nastavení, které jsou obsaženy v jednom souboru jsou načtena a uložena jako celek. Ukládání nastavení do samostatných souborů pro často používané a zřídka používané skupiny může ušetřit čas při načítání a ukládání nastavení.

Například můžete přidat soubor jako *SpecialSettings.settings* do projektu. Během vaší `SpecialSettings` třída není vystaveno v `My` obor názvů, **zobrazit kód** může číst, která obsahuje soubor s vlastním nastavením `Partial Class SpecialSettings`.

**Návrháře nastavení** nejprve hledá *Settings.settings* souboru, který vytvoří systém projektu; tento soubor je výchozí soubor, který **Návrháře projektu** Zobrazí **nastavení** kartu. *Settings.Settings* se nachází v *Můj projekt* složku pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty a *vlastnosti* složku pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty. **Návrháře projektu** pak vyhledá ostatní soubory nastavení v kořenové složce projektu. Proto byste měli existuje umístit soubor s vlastním nastavením. Pokud chcete přidat *.settings* soubor jinde v projektu, **Návrháře projektu** nebude schopen jej vyhledat.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Přístup nebo změna nastavení aplikace za běhu v jazyce Visual Basic

V projektech Visual Basicu můžete přistupujete k nastavení aplikace za běhu pomocí `My.Settings` objektu. Na **nastavení** stránky, klikněte na tlačítko **zobrazení kódu** tlačítko Zobrazit *Settings.vb* souboru. *Settings.vb* definuje `Settings` třídu, která umožňuje zpracování těchto událostí na třídě nastavení: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Všimněte si, `Settings` třídy v *Settings.vb* je částečná třída zobrazující pouze uživatele kód, nikoli celou generovanou třídu. Další informace o přístup k nastavení aplikace s použitím `My.Settings` objektu, najdete v článku [přístup k nastavení aplikace (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Hodnoty nastavení rozsahu uživatele, které změny uživatelů v době běhu (například umístění formuláře) jsou uložené v *user.config* souboru. Všimněte si, že výchozí hodnoty jsou stále uloženy v *app.config*.

Pokud nastavení rozsahu uživatele se změní za běhu, třeba při testování aplikace a chcete resetovat tato nastavení na výchozí hodnoty, klikněte na tlačítko **synchronizovat** tlačítko.

Důrazně doporučujeme používat `My.Settings` objektu a ve výchozím nastavení *.settings* souboru pro přístup k nastavení. Důvodem je, že můžete použít **návrháře nastavení** k přiřazení vlastností do nastavení a kromě toho také uživatelské nastavení je automaticky uloženo před vypnutím aplikace. Ale aplikace Visual Basic můžete přístup k nastavení přímo. V takovém případě budete muset získat přístup `MySettings` třídy a používat vlastní *.settings* souboru v kořenovém adresáři projektu. Musíte uložit nastavení uživatele před ukončením aplikace, jako byste to udělali pro aplikaci v C#; je to popsané v následující části.

## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Přístup nebo změna nastavení aplikace za běhu v jazyce C# #

V jiných jazycích než jazyka Visual Basic, jako je C#, je nutné přejít `Settings` třídy přímo, jak je znázorněno v následujícím [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] příklad.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Musíte explicitně volat `Save` metoda této obálkové třídy s cílem zachovat nastavení uživatele. Obvykle to provedete `Closing` obslužná rutina události hlavního formuláře. Následující příklad jazyka C# ukazuje volání `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Obecné informace o přístupu k nastavení aplikace prostřednictvím `Settings` najdete v tématu [přehled nastavení aplikace (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Informace o provádění iterací přes nastavení naleznete v tomto [příspěvek na fóru](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Viz také:

- [Přístup k nastavení aplikace (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
