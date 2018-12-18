---
title: Podpora pro uživatelská nastavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 445f95b1c52b5ada41918cf0f7d8120d912c209f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759893"
---
# <a name="support-for-user-settings"></a>Podpora pro uživatelská nastavení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage může definovat jeden nebo více kategorií nastavení, které jsou skupiny proměnných stavu, které se zachovávají po kliknutí **Importovat/exportovat nastavení** příkaz **nástroje** nabídky. Pokud chcete povolit tento trvalost, použijte nastavení rozhraní API v [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 Položky registru, který se označuje jako bod vlastní nastavení a identifikátor GUID definuje kategorie nastavení na VSPackage. VSPackage může podporovat více kategorie nastavení, každý definovaný pomocí vlastního nastavení bodu.  
  
-   Implementace nastavení, které jsou založeny na sestavení vzájemné spolupráce (pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> rozhraní) by měl vytvořit vlastní nastavení bodu pomocí úpravy registru nebo pomocí skriptu registrátoru (souboru .rgs). Další informace najdete v tématu [vytváření skriptů registrátoru](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
-   Kód, který používá Managed Package Framework (MPF) by měl vytvořit vlastní nastavení bodů připojením <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> VSPackage pro každý bod vlastní nastavení.  
  
     Pokud jeden VSPackage podporuje několik bodů vlastní nastavení, každý vlastního nastavení bodu je implementováno samostatné třídy a každé registraci jedinečnou instanci <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třídy. V důsledku toho nastavení implementující třída může podporovat více než jednu kategorii nastavení.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Podrobnosti položky registru bodu vlastní nastavení  
 Vlastní nastavení body se vytvoří v registru v následujícím umístění: HKLM\Software\Microsoft\VisualStudio\\*\<verze >* \UserSettings\\`<CSPName>`, kde `<CSPName>` je název vlastního nastavení bodu VSPackage podporuje a  *\<verze >* je verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], například 8.0.  
  
> [!NOTE]
>  Kořenová cesta HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<verze >* lze přepsat pomocí alternativního root, kdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je integrované vývojové prostředí (IDE) inicializovat. Další informace najdete v tématu [přepínače příkazového řádku](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Struktura položky registru je znázorněno níže:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<verze >* \UserSettings\  
  
 `<CSPName`> = s: 12345 #.  
  
 Balíček = "{XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
 Kategorie = "{YYYYYY YYYY rrrr rrrr YYYYYYYYY}.  
  
 ResourcePackage = "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}.  
  
 AlternateParent = CategoryName  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|(Výchozí)|REG_SZ|Název vlastního nastavení bodu|Název klíče, `<CSPName`>, je nelokalizovaný název vlastního nastavení bodu.<br /><br /> Pro implementace podle MPF, je tím, že zkombinujete získat název klíče `categoryName` a `objectName` argumenty <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktor do `categoryName_objectName`.<br /><br /> Klíč může být prázdný nebo měl obsahovat ID odkazu na lokalizovaný řetězec v satelitní knihovně DLL. Tato hodnota pochází z `objectNameResourceID` argument <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktoru.|  
|Balíček|REG_SZ|GUID|Identifikátor GUID sady VSPackage, která implementuje vlastního nastavení bodu.<br /><br /> Implementace založené na používání MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třídy, použijte konstruktoru `objectType` argument, který obsahuje sady VSPackage <xref:System.Type> a reflexe získat tuto hodnotu.|  
|Kategorie|REG_SZ|GUID|Identifikátor GUID identifikující kategorie nastavení.<br /><br /> Pro implementace podle sestavení vzájemné spolupráce, tato hodnota může být libovolně zvolený identifikátor GUID, který [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí se předá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metody. Všechny implementace z těchto dvou metod by měl ověřit své argumenty identifikátor GUID.<br /><br /> Pro implementace podle MPF, je tento identifikátor GUID získané <xref:System.Type> implementace třídy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mechanismus nastavení.|  
|ResourcePackage|REG_SZ|GUID|Volitelné.<br /><br /> Cestu k satelitní knihovny DLL obsahující lokalizované řetězce, pokud je neposkytuje implementaci VSPackage.<br /><br /> MPF používá reflexi získat správný zdroj balíčku VSPackage, takže <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> třída nemá nastaven tento argument.|  
|AlternateParent|REG_SZ|Název složky v rámci stránky Možnosti nástrojů obsahující tento bod vlastní nastavení.|Volitelné.<br /><br /> Tato hodnota musíte nastavit pouze v případě, že nastavení implementace podporuje **možnosti nástrojů** stránky, které používají mechanismus trvalosti v [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] místo mechanismus v modelu automatizace pro uložení stavu.<br /><br /> V těchto případech je hodnota v klíči AlternateParent `topic` část `topic.sub-topic` řetězec používaný k identifikaci konkrétní **ToolsOptions** stránky. Třeba **ToolsOptions** stránky `"TextEditor.Basic"` bude hodnota AlternateParent `"TextEditor"`.<br /><br /> Když <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generuje vlastního nastavení bodu, je stejný jako název kategorie.|

