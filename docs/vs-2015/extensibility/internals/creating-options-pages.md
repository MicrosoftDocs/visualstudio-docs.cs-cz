---
title: Vytvoření stránek možnosti | Dokumentace Microsoftu
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
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 076c4934fe4f81bd56edc70356ecdcc1101456e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760332"
---
# <a name="creating-options-pages"></a>Vytvoření stránek Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spravovaného balíčku rozhraní .NET framework, třídy odvozené z <xref:Microsoft.VisualStudio.Shell.DialogPage> rozšířit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí tak, že přidáte **možnosti** stránky v části **nástroje** nabídky.  
  
 Implementaci objektu dané **– možnost Nástroje** stránky je přidružený k konkrétní rozšíření VSPackages podle <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objektu.  
  
 Protože prostředí vytvoří instanci objektu implementace konkrétní **možnosti nástrojů** stránce při této konkrétní stránce se zobrazí v integrovaném vývojovém prostředí:  
  
-   A **– možnost Nástroje** stránka by měla být implementována na vlastní objekt a ne na objekt implementující VSPackage.  
  
-   Objekt nelze implementovat více **možnosti nástrojů** stránky.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrace jako poskytovatel stránky Možnosti nástrojů  
 Konfigurace balíčku VSPackage podpůrné uživatele prostřednictvím **možnosti nástrojů** stránky určuje objekty, které poskytuje **možnosti nástrojů** stránky s použitím instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> u <xref:Microsoft.VisualStudio.Shell.Package>implementace.  
  
 Musí být jedna instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pro každý <xref:Microsoft.VisualStudio.Shell.DialogPage>-odvozený typ, který implementuje **možnosti nástrojů** stránky.  
  
 Každá instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> používá typ, který implementuje **možnosti nástrojů** stránce, řetězce, které obsahují kategorie a podkategorie slouží k identifikaci **možnosti nástrojů** stránky a prostředků informace o registraci typu jako poskytuje **možnosti nástrojů** stránky.  
  
## <a name="persisting-tools-options-page-state"></a>Zachování stavu stránky Možnosti nástrojů  
 Pokud **možnosti nástrojů** stránka provádění je registrován s povolenou podporou mezipaměti o automatizaci, rozhraní IDE zachová stav stránky spolu s ostatními všechny **možnosti nástrojů** stránky.  
  
 VSPackage můžete spravovat své vlastní trvalosti pomocí <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. By měla sloužit pouze jednu nebo jiná metoda typu stálosti.  
  
## <a name="implementing-dialogpage-class"></a>Implementace třídy DialogPage třídy  
 Objekt, který poskytuje na VSPackage provádění <xref:Microsoft.VisualStudio.Shell.DialogPage>-odvozený typ může využívat následující zděděné funkce:  
  
- Výchozí uživatelské rozhraní okna.  
  
- A výchozí mechanismus trvalosti, které jsou k dispozici buď pokud <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> aplikován na třídu, nebo pokud <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> je nastavena na `true` pro <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , která je použita na třídu.  
  
- Podpora automatizace.  
  
  Minimální požadavky pro implementaci objekt **možnosti nástrojů** stránky <xref:Microsoft.VisualStudio.Shell.DialogPage> , je přidání veřejné vlastnosti.  
  
  Pokud třída správně zaregistrovaný jako **možnosti nástrojů** stránce poskytovatele, pak jeho veřejné vlastnosti jsou k dispozici na **možnosti** část **nástroje** nabídce ve formuláři mřížku vlastností.  
  
  Všechny tyto funkce výchozí lze přepsat. Například k vytváření sofistikovanějších uživatelského rozhraní vyžaduje pouze výchozí implementaci přepsání <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Příklad  
 Dále je jednoduchá "hello world" implementace stránky možnosti. Přidáním následujícího kódu do výchozí projekt vytvořen pomocí šablony Visual Studio balíček s **příkazu nabídky** zaškrtnutou možnost adekvátní vám ukáže funkci stránky možnost.  
  
### <a name="description"></a>Popis  
 Následující třídy definuje minimální stránka možností "hello world". Při otevření, může uživatel nastavit veřejnosti `HelloWorld` vlastnost v mřížce vlastností.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Popis  
 Použití třídy balíčku následující atribut zpřístupní možnosti stránky při načtení balíčku. Čísla jsou libovolného prostředku ID kategorie a na stránce a logickou hodnotu na konci Určuje, zda stránky podporuje služby automation.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Popis  
 Následující obslužná rutina události zobrazí výsledky v závislosti na hodnotě vlastnosti nastavit na stránce Možnosti. Používá <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metoda s výsledkem explicitně přetypován na typ stránky vlastní možnost získat přístup k vlastnostem vystavené na stránce.  
  
 V případě projektů vygenerovaný balíček šablony, voláním této funkce z `MenuItemCallback` přidána funkce, aby se připojil do výchozí příkaz **nástroje** nabídky.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření uživatelských nastavení a možnosti](../../extensibility/extending-user-settings-and-options.md)   
 [Podpora automatizace pro stránky Možnosti](../../extensibility/internals/automation-support-for-options-pages.md)

