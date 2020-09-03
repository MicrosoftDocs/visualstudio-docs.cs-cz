---
title: Podpora uživatelských nastavení | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704781"
---
# <a name="support-for-user-settings"></a>Podpora pro uživatelská nastavení
VSPackage může definovat jednu nebo více kategorií nastavení, což jsou skupiny proměnných stavu, které jsou trvalé, když uživatel zvolí příkaz **Import/Export nastavení** v nabídce **nástroje** . Pro povolení této trvalosti použijete rozhraní API nastavení v [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Položka registru, která se označuje jako bod vlastního nastavení a identifikátor GUID definuje kategorii nastavení VSPackage. VSPackage může podporovat více kategorií nastavení, které jsou definovány vlastním bodem nastavení.

- Implementace nastavení, které jsou založeny na definičních sestaveních (pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> rozhraní), by měly vytvořit vlastní bod nastavení buď úpravou registru, nebo použitím skriptu registrátora (soubor. rgs). Další informace najdete v tématu [vytváření skriptů registrátora](/cpp/atl/creating-registrar-scripts).

- Kód, který používá sadu Managed Package Framework (MPF), by měl vytvořit vlastní body nastavení připojením <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> k VSPackage pro každý vlastní bod nastavení.

     Pokud jeden VSPackage podporuje několik vlastních bodů nastavení, každý vlastní bod nastavení je implementován samostatnou třídou a každý je zaregistrován jedinečnou instancí <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třídy. V důsledku toho může třída implementující třídu podporovat více než jednu kategorii nastavení.

## <a name="custom-settings-point-registry-entry-details"></a>Podrobnosti položky registru pro vlastní nastavení
 Body vlastního nastavení jsou vytvořeny v položce registru v následujícím umístění: HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` , kde `<CSPName>` je název vlastního bodu nastavení, který VSPackage podporuje, a *\<Version>* je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , například 8,0.

> [!NOTE]
> Kořenovou cestu HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* lze přepsat alternativním kořenem při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inicializaci integrovaného vývojového prostředí (IDE). Další informace najdete v tématu [přepínače příkazového řádku](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Struktura položky registru je znázorněna níže:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= s ' #12345 '

 Package = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX} '

 Kategorie = ' {YYYYYY YYYY yyyy yyyy YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = CategoryName

| Název | Typ | Data | Popis |
|-----------------|--------| - | - |
| (Výchozí) | REG_SZ | Název vlastního bodu nastavení | Název klíče, `<CSPName`>, je nemístní název vlastního bodu nastavení.<br /><br /> U implementací založených na klíči MPF je název klíče získán kombinací `categoryName` `objectName` argumentů a argumentů <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktoru do `categoryName_objectName` .<br /><br /> Klíč může být prázdný nebo může obsahovat ID odkazu na lokalizovaný řetězec v satelitní knihovně DLL. Tato hodnota je získána z `objectNameResourceID` argumentu <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktoru. |
| Balíček | REG_SZ | Identifikátor GUID | Identifikátor GUID VSPackage, který implementuje vlastní bod nastavení.<br /><br /> Implementace založené na hodnotě MPF využívající <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třídu použijte `objectType` <xref:System.Type> k získání této hodnoty argument konstruktoru obsahující VSPackage a reflexi. |
| Kategorie | REG_SZ | Identifikátor GUID | Identifikátor GUID identifikující kategorii nastavení<br /><br /> U implementací založených na definičních sestaveních může být tato hodnota libovolně zvolený identifikátor GUID, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní IDE předává do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metody. Všechny implementace těchto dvou metod by měly ověřit argumenty identifikátoru GUID.<br /><br /> U implementací na základě hodnoty MPF je tento identifikátor GUID získán <xref:System.Type> z třídy, která implementuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mechanismus nastavení. |
| ResourcePackage | REG_SZ | Identifikátor GUID | Nepovinný parametr.<br /><br /> Cesta k satelitní knihovně DLL obsahující lokalizované řetězce, pokud implementující VSPackage nedodá.<br /><br /> Parametr MPF používá reflexi pro získání správného prostředku VSPackage, takže <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Třída nenastavuje tento argument. |
| AlternateParent | REG_SZ | Název složky na stránce Možnosti nástrojů, která obsahuje tento vlastní bod nastavení. | Nepovinný parametr.<br /><br /> Tuto hodnotu je nutné nastavit pouze v případě, že implementace nastavení podporuje stránky **možností nástrojů** , které používají mechanismus trvalosti [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] místo mechanismu v modelu automatizace pro uložení stavu.<br /><br /> V těchto případech je hodnotou v klíči AlternateParent oddíl řetězce, který `topic` `topic.sub-topic` slouží k identifikaci konkrétní stránky **ToolsOptions** . Například pro stránku **ToolsOptions** bude `"TextEditor.Basic"` hodnota AlternateParent `"TextEditor"` .<br /><br /> Když <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generuje vlastní bod nastavení, je stejný jako název kategorie. |
