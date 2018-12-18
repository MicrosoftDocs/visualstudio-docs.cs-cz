---
title: Vytvoření stránek možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 236d9a0be82885bdf8040c97601429279e74dd15
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949640"
---
# <a name="create-options-pages"></a>Vytvoření stránky Možnosti
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spravovaného balíčku rozhraní .NET framework, třídy odvozené z <xref:Microsoft.VisualStudio.Shell.DialogPage> rozšířit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí tak, že přidáte **možnosti** stránky v části **nástroje** nabídky.  
  
 Implementaci objektu dané **– možnost Nástroje** stránky je přidružený k konkrétní rozšíření VSPackages podle <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objektu.  
  
 Protože prostředí vytvoří instanci objektu implementace konkrétní **možnosti nástrojů** stránce při této konkrétní stránce se zobrazí v integrovaném vývojovém prostředí:  
  
-   A **– možnost Nástroje** stránka by měla být implementována na vlastní objekt a ne na objekt implementující VSPackage.  
  
-   Objekt nelze implementovat více **možnosti nástrojů** stránky.  
  
## <a name="register-as-a-tools-options-page-provider"></a>Zaregistrujte se jako zprostředkovatel stránky Možnosti nástrojů  
 Konfigurace balíčku VSPackage podpůrné uživatele prostřednictvím **možnosti nástrojů** stránky určuje objekty, které poskytuje **možnosti nástrojů** stránky s použitím instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> u <xref:Microsoft.VisualStudio.Shell.Package>implementace.  
  
 Musí být jedna instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pro každý <xref:Microsoft.VisualStudio.Shell.DialogPage>-odvozený typ, který implementuje **možnosti nástrojů** stránky.  
  
 Každá instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> používá typ, který implementuje **možnosti nástrojů** stránce, řetězce, které obsahují kategorie a podkategorie slouží k identifikaci **možnosti nástrojů** stránky a prostředků informace o registraci typu jako poskytuje **možnosti nástrojů** stránky.  
  
## <a name="persist-tools-options-page-state"></a>Zachovat stav stránky Možnosti nástrojů  
 Pokud **možnosti nástrojů** stránka provádění je registrován s povolenou podporou mezipaměti o automatizaci, rozhraní IDE zachová stav stránky spolu s ostatními všechny **možnosti nástrojů** stránky.  
  
 VSPackage můžete spravovat své vlastní trvalosti pomocí <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. By měla sloužit pouze jednu nebo jiná metoda typu stálosti.  
  
## <a name="implement-dialogpage-class"></a>Implementace třídy DialogPage třídy  
 Objekt, který poskytuje na VSPackage provádění <xref:Microsoft.VisualStudio.Shell.DialogPage>-odvozený typ může využívat následující zděděné funkce:  
  
- Výchozí uživatelské rozhraní okna.  
  
- A výchozí mechanismus trvalosti, které jsou k dispozici buď pokud <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> aplikován na třídu, nebo pokud <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> je nastavena na `true` pro <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , která je použita na třídu.  
  
- Podpora automatizace.  
  
  Minimální požadavky pro implementaci objekt **možnosti nástrojů** stránky <xref:Microsoft.VisualStudio.Shell.DialogPage> , je přidání veřejné vlastnosti.  
  
  Pokud třída správně zaregistrovaný jako **možnosti nástrojů** stránce poskytovatele, pak jeho veřejné vlastnosti jsou k dispozici na **možnosti** část **nástroje** nabídce ve formuláři mřížku vlastností.  
  
  Všechny tyto funkce výchozí lze přepsat. Například k vytváření sofistikovanějších uživatelského rozhraní vyžaduje pouze výchozí implementaci přepsání <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Příklad  
 Dále je jednoduchý "Hello world" implementace stránky možnosti. Přidáním následujícího kódu do projektu výchozí vytvořených šablonou sady Visual Studio balíček s **příkazu nabídky** zaškrtnutou možnost adekvátní vám ukáže funkci stránky možnost.  
  
### <a name="description"></a>Popis  
 Následující třídy definuje stránky Možnosti minimální "Hello world". Při otevření, může uživatel nastavit veřejnosti `HelloWorld` vlastnost v mřížce vlastností.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Popis  
 Použití třídy balíčku následující atribut zpřístupní možnosti stránky při načtení balíčku. Čísla jsou libovolného prostředku ID kategorie a na stránce a logickou hodnotu na konci Určuje, zda stránky podporuje služby automation.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Popis  
 Následující obslužná rutina události zobrazí výsledky v závislosti na hodnotě vlastnosti nastavit na stránce Možnosti. Používá <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metoda s výsledkem explicitně přetypován na typ stránky vlastní možnost získat přístup k vlastnostem vystavené na stránce.  
  
 V případě projektů vygenerovaný balíček šablony, voláním této funkce z `MenuItemCallback` přidána funkce, aby se připojil do výchozí příkaz **nástroje** nabídky.  
  
### <a name="code"></a>Kód  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Viz také:  
 [Rozšířit možnosti a nastavení uživatele](../../extensibility/extending-user-settings-and-options.md)   
 [Podpora automatizace pro stránky Možnosti](../../extensibility/internals/automation-support-for-options-pages.md)