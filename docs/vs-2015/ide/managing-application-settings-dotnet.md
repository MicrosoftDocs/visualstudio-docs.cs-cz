---
title: Správa nastavení aplikace (.NET) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac4f670b813970d027925b681a2e3211e1898e1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866126"
---
# <a name="managing-application-settings-net"></a>Správa nastavení aplikace (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení aplikace umožňují uložení informací aplikace dynamicky. Nastavení vám umožňují ukládat informace na klientský počítač, který by neměl být zařazen do kódu aplikace (například připojovací řetězec), uživatelských předvoleb a dalších informací, které potřebujete v době běhu.  
  
 Nastavení aplikace nahradí dynamické vlastnosti použité v dřívějších verzích sady Visual Studio.  
  
 Každé nastavení aplikace musí mít jedinečný název. Název může obsahovat libovolnou kombinaci písmen, čísel nebo podtržítek, která nezačíná řetězcem číslo a nesmí obsahovat mezery. Název lze změnit prostřednictvím `Name` vlastnost.  
  
 Nastavení aplikace lze uložit jako libovolný typ dat, který lze serializovat do formátu XML nebo má `TypeConverter` , který implementuje `ToString` / `FromString`. Nejběžnější typy jsou `String`, `Integer`, a `Boolean`, ale můžete také uložit hodnoty jako <xref:System.Drawing.Color>, <xref:System.Object>, nebo jako připojovací řetězec.  
  
 Nastavení aplikace také obsahují hodnotu. Tato hodnota nastavená s **hodnotu** vlastnost a musí odpovídat datovému typu nastavení.  
  
 Kromě toho nastavení aplikace mohou být vázány na vlastnost formuláře nebo ovládacího prvku v době návrhu.  
  
 Existují dva typy nastavení aplikace založené na rozsahu:  
  
- Nastavení oboru aplikace lze použít pro informace, jako je adresa URL pro webovou službu nebo připojovací řetězec databáze. Tyto hodnoty jsou spojeny s aplikací. Proto je uživatelé nemohou změnit za běhu.  
  
- Nastavení s rozsahem uživatele lze použít pro informace, jako jsou například uchování poslední pozice formuláře nebo předvoleb písma. Uživatelé mohou změnit tyto hodnoty v době běhu.  
  
  Typ nastavení můžete změnit pomocí **oboru** vlastnost.  
  
  Systém projektu ukládá nastavení aplikace ve dvou souborech XML: app.config soubor, který je vytvořen v době návrhu, když vytvoříte první nastavení aplikace; a user.config soubor, který je vytvořen v době běhu, když uživatel, který spouští aplikaci změní hodnotu nastavení některého uživatele. Všimněte si, že změny v nastavení uživatele nejsou zapsány na disk, pokud aplikace konkrétně nevolá metodu, chcete-li to provést.  
  
## <a name="creating-application-settings-at-design-time"></a>Vytvoření nastavení aplikace v době návrhu  
 V době návrhu, můžete vytvořit nastavení aplikace dvěma způsoby: pomocí **nastavení** stránku **Návrháře projektu**, nebo pomocí **vlastnosti** okna pro formulář nebo ovládací prvek, který umožňuje svázat nastavení vlastnosti.  
  
 Když vytvoříte nastavení s rozsahem aplikace (například připojovací řetězec databáze nebo odkaz na prostředky serveru), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uloží do app.config `<applicationSettings>` značky. (Připojovací řetězce jsou uloženy v rámci `<connectionStrings>` značka.)  
  
 Když vytvoříte nastavení s rozsahem uživatele (například výchozí písmo, domovská stránka nebo velikost okna), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uloží do app.config `<userSettings>` značky.  
  
> [!IMPORTANT]
>  Při ukládání připojovacích řetězců v app.config byste měli podniknout opatření k zamezení odhalení citlivých informací, jako jsou hesla nebo cesty k serveru, v připojovacím řetězci.  
>   
>  Pokud budete postupovat informace o připojovacím řetězci z externího zdroje, jako je například uživatelské zadání ID uživatele a heslo, musíte být opatrní a zkontrolujte, že hodnoty, které můžete použít k vytvoření připojení řetězec neobsahují další parametry připojovacího řetězce která mění chování vašeho připojení.  
>   
>  Zvažte použití funkce Protected Configuration pro šifrování citlivých informací v konfiguračním souboru. Zobrazit [chrání informace o připojení](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) Další informace.  
  
> [!NOTE]
>  Protože neexistuje žádný model konfiguračního souboru pro knihovny tříd, nastavení aplikace nelze aplikovat na projekty knihovny tříd. Výjimkou je Visual Studio Tools for Office DLL projekt, který může mít konfigurační soubor.  
  
## <a name="using-customized-settings-files"></a>Použití vlastních souborů nastavení  
 Soubory vlastního nastavení můžete přidat do projektu pro pohodlné řízení skupin nastavení. Nastavení, které jsou obsaženy v jednom souboru jsou načtena a uložena jako celek. Proto možnost Uložit nastavení do samostatných souborů pro často používané a zřídka používané skupiny může ušetřit čas při načítání a ukládání nastavení.  
  
 Můžete například přidat soubor jako je SpecialSettings.settings do vašeho projektu. Během vaší `SpecialSettings` třída není vystaveno v `My` obor názvů, **zobrazit kód** může číst, která obsahuje soubor s vlastním nastavením `Partial Class SpecialSettings`.  
  
 Návrhář nastavení nejprve hledá soubor Settings.settings, který vytvoří systém projektu; Toto je výchozí soubor, který Návrhář projektu zobrazí v **nastavení** kartu. Settings.Settings je umístěn ve složce Můj projekt pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty a ve složce vlastnosti pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty. Návrhář projektu pak vyhledá ostatní soubory nastavení v kořenové složce projektu. Proto byste měli existuje umístit soubor s vlastním nastavením. Pokud přidáte soubor .settings jinde v projektu, Návrhář projektu nebude schopen jej vyhledat.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Přístup nebo změna nastavení aplikace za běhu v jazyce Visual Basic  
 V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, dostanete nastavení aplikace za běhu pomocí `My.Settings` objektu. Na **nastavení** stránky, klikněte na tlačítko **zobrazení kódu** tlačítko k zobrazení souboru Settings.vb. Settings.vb definuje `Settings` třídu, která umožňuje zpracování těchto událostí na třídě nastavení: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Všimněte si, že `Settings` třídy v Settings.vb je částečná třída zobrazující pouze uživatele kód, nikoli celou generovanou třídu. Další informace o přístup k nastavení aplikace s použitím `My.Settings` objektu, najdete v článku [přístup k nastavení aplikace](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).  
  
 Hodnoty nastavení rozsahu uživatele, které uživatel změní za běhu (například umístění formuláře) jsou uloženy v souboru user.config. Všimněte si, že výchozí hodnoty jsou stále uloženy v souboru app.config.  
  
 Pokud jste změnili nastavení rozsahu uživatele za běhu, třeba při testování aplikace a chcete resetovat tato nastavení na výchozí hodnoty, klikněte na tlačítko **synchronizovat** tlačítko.  
  
 Důrazně doporučujeme používat `My.Settings` objektu a výchozí soubor .settings k přístupu k nastavení. Je to proto, že používáte návrháře nastavení k přiřazení vlastností do nastavení a kromě toho nastavení uživatele je automaticky uloženo před vypnutím aplikace. Však vaše [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplikace získá přístup k nastavení přímo. V takovém případě budete muset získat přístup `MySettings` třídy a použít vlastní soubor .settings v kořenové složce projektu. Musíte také uložit nastavení uživatele před ukončením aplikace, jako byste to udělali pro aplikaci v C#; je to popsané v následující části.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Přístup nebo změna nastavení aplikace za běhu v jazyce Visual C#  
 V jazycích jiných než [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], jako například [!INCLUDE[csprcs](../includes/csprcs-md.md)], musí přejít `Settings` třídy přímo, jak je znázorněno v následujícím [!INCLUDE[csprcs](../includes/csprcs-md.md)] příklad.  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 Musíte také explicitně volat `Save` metoda této obálkové třídy s cílem zachovat nastavení uživatele. Obvykle to provedete `Closing` obslužná rutina události hlavního formuláře. Následující [!INCLUDE[csprcs](../includes/csprcs-md.md)] příklad ukazuje volání `Save` metody.  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Obecné informace o přístupu k nastavení aplikace prostřednictvím `Settings` najdete v tématu [přehled nastavení aplikace](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Informace o provádění iterací přes nastavení naleznete v tomto [příspěvek na fóru](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Viz také  
 [Přístup k nastavení aplikace](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)



