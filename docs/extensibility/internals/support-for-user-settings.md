---
title: Podpora uživatelských nastavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704781"
---
# <a name="support-for-user-settings"></a>Podpora pro uživatelská nastavení
VSPackage může definovat jednu nebo více kategorií nastavení, což jsou skupiny proměnných stavu, které přetrvávají, když uživatel zvolí příkaz **Nastavení importu nebo exportu** v nabídce **Nástroje.** Chcete-li povolit tuto trvalost, použijte [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]nastavení API v .

 Položka registru, která je označována jako bod vlastního nastavení a identifikátor GUID definuje kategorii nastavení balíčku VSPackage. VSPackage může podporovat více kategorií nastavení, z nichž každá je definována bodem vlastního nastavení.

- Implementace nastavení, která jsou založena na interop <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> sestavení (pomocí rozhraní) by měla vytvořit vlastní bod nastavení buď úpravou registru nebo pomocí skriptu registrátora (.rgs soubor). Další informace naleznete [v tématu Vytváření skriptů registrátorů](/cpp/atl/creating-registrar-scripts).

- Kód, který používá rozhraní MPF (Managed Package Framework) <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> by měl vytvořit body vlastního nastavení připojením a k balíčku VSPackage pro každý bod vlastního nastavení.

     Pokud jeden VSPackage podporuje několik bodů vlastního nastavení, každý bod vlastního nastavení je implementován <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> samostatnou třídou a každý je registrován jedinečnou instancí třídy. V důsledku toho nastavení implementující třídu může podporovat více než jednu kategorii nastavení.

## <a name="custom-settings-point-registry-entry-details"></a>Podrobnosti o položce registru vlastního bodu nastavení
 Body vlastního nastavení jsou vytvořeny v položce registru v následujícím umístění:\\*\< *HKLM\Software\Microsoft\VisualStudio Version>\UserSettings\\`<CSPName>`, kde `<CSPName>` je název bodu vlastního nastavení, který podporuje VSPackage a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<verze>* je verze aplikace , například 8.0.

> [!NOTE]
> Kořenová cesta HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* lze přepsat alternativním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kořenem při inicializování integrovaného vývojového prostředí (IDE). Další informace naleznete v [tématu Command-Line Switches](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Struktura položky registru je znázorněna níže:

 HKLM\Software\Microsoft\VisualStudio\\*\<Version>* \UserSettings\

 `<CSPName`>= s '#12345'

 Balíček = {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Kategorie = '{YYYYYY YYYY YYYY YYYYYYYYYYY}'

 ResourcePackage = '{Zzzzz Zzzz Zzzz Zzzz zzzzzzz}'

 AlternateParent = Název_kategorie

| Name (Název) | Typ | Data | Popis |
|-----------------|--------| - | - |
| (Výchozí) | REG_SZ | Název bodu vlastního nastavení | Název klíče, `<CSPName`>, je nelokalizovaný název bodu vlastního nastavení.<br /><br /> Pro implementace založené na MPF, název klíče je získán `categoryName` `objectName` kombinací a <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> argumenty `categoryName_objectName`konstruktoru do .<br /><br /> Klíč může být prázdný nebo může obsahovat ID odkazu na lokalizovaný řetězec v satelitní dll. Tato hodnota je `objectNameResourceID` získána <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> z argumentu konstruktoru. |
| Balíček | REG_SZ | GUID | Identifikátor GUID balíčku VSPackage, který implementuje bod vlastního nastavení.<br /><br /> Implementace založené na MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> pomocí třídy, použijte `objectType` argument konstruktoru obsahující <xref:System.Type> VSPackage a reflexe získat tuto hodnotu. |
| Kategorie | REG_SZ | GUID | IDENTIFIKÁTOR GUID identifikující kategorii nastavení.<br /><br /> Pro implementace založené na interop sestavení, tato hodnota může být libovolně [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zvolené GUID, který IDE předává <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metody. Všechny implementace těchto dvou metod by měly ověřit jejich argumenty GUID.<br /><br /> Pro implementace založené na MPF tento identifikátor <xref:System.Type> GUID je získán [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] třídy implementující mechanismus nastavení. |
| Balíček prostředků | REG_SZ | GUID | Nepovinný parametr.<br /><br /> Cesta k satelitní dll obsahující lokalizované řetězce, pokud implementující VSPackage neposkytuje.<br /><br /> MPF používá reflexe získat správný prostředek VSPackage, takže <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třída nenastaví tento argument. |
| Alternativní rodič | REG_SZ | Název složky na stránce Možnosti nástrojů obsahující tento bod vlastního nastavení. | Nepovinný parametr.<br /><br /> Tuto hodnotu je nutné nastavit pouze v případě, že implementace [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nastavení podporuje stránky **Tools Options,** které používají mechanismus trvalosti v mechanismu, nikoli mechanismu s mechanismem v modelu automatizace k uložení stavu.<br /><br /> V těchto případech je hodnota v klíči AlternateParent `topic` část `topic.sub-topic` řetězce, který slouží k identifikaci konkrétní **ToolsOptions** stránky. Například pro **ToolsOptions** `"TextEditor.Basic"` stránku hodnota AlternateParent `"TextEditor"`by .<br /><br /> Když <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generuje bod vlastního nastavení, je stejný jako název kategorie. |
