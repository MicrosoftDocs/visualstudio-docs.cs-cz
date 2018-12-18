---
title: Lokalizace řešení služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba02d8811fc6633a55e06ae63c9399c70f59634f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120279"
---
# <a name="localize-sharepoint-solutions"></a>Lokalizace řešení služby SharePoint

  Příprava aplikace tak, aby bylo možné po celém světě proces se označuje jako lokalizace. Lokalizace je překlad prostředků do konkrétní jazykové verze. Další informace najdete v tématu [Globalizing a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications). Toto téma poskytuje přehled o tom, jak lokalizace řešení služby SharePoint.  
  
 O lokalizaci řešení, odeberte pevně řetězce z kódu a je abstraktní do zdrojových souborů. Soubor prostředků je [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]– na základě soubor s *RESX* rozšíření. Soubor prostředků obsahuje přeložené verze řetězce použité v řešení. Další informace najdete v tématu [prostředky v aplikacích](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Přidejte pouze řetězcové prostředky do souborů prostředků řešení služby SharePoint. I když editoru prostředků umožňuje přidat jiné než řetězec prostředky, jiné než řetězec prostředky nenasazujte do služby SharePoint.  
  
## <a name="resource-files"></a>Soubory prostředků
 Existují tři druhy soubory prostředků: výchozí, jazykově neutrální a konkrétní jazyk.  
  
|Typ souboru prostředků|Popis|  
|------------------------|-----------------|  
|Výchozí|Také označované jako prostředek záložní soubory prostředků výchozí obsahují řetězce lokalizovaný pro výchozí jazykovou verzi, jako je angličtina. Používají se, pokud lze nalézt žádné soubory lokalizovaný prostředek pro určený jazyk. Výchozí prostředky nemají samostatné soubory, jsou uložené v hlavní aplikaci sestavení.|  
|Jazykově neutrální|Soubor prostředků, který obsahuje řetězce lokalizovaný pro jazyk, ale není konkrétní jazykové verze. Například "fr" pro francouzštinu.|  
|Konkrétní jazyk|Soubor prostředků, který obsahuje řetězce lokalizovaný pro jazyk a jazykovou verzi. Například "fr-CA" pro francouzština (Kanada).|  
  
 Další informace najdete v tématu [hierarchická organizace zdrojů pro lokalizaci](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Pokud chcete zadat výchozí soubory prostředků do projektů služby SharePoint, které vyvíjíte v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], zvolte **neutrální jazyk (neutrální země)** v seznamu jazykovou verzi **přidat prostředek** dialogu, kdy jste Přidání zdrojového souboru.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalizace řešení služby SharePoint Visual Studio
 Při lokalizaci berte řešení, byste měli zvážit všechny textové informace, které řešení zobrazí uživatelům. Informační zprávy a chybové zprávy a [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] je nutné přeložit řetězce a tyto překlady umístěny soubory prostředků.  
  
 Každý řetězec v souboru prostředků má jedinečný identifikátor. Použijte stejný identifikátor přeložené řetězce do každého souboru prostředků. Například pokud je "Řetězec1" identifikátor pro první řetězec v souboru prostředků výchozí, použijte stejný identifikátor pro první řetězec v souborech prostředků pro specifický jazyk.  
  
 Existují tři oblasti obvykle lokalizace v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikací služby SharePoint: funkce, značek stránky ASPX a kódu. Pro účely obrázku v následujících částech předpokládá, že máte řešení služby SharePoint, kterou chcete lokalizace do němčina a japonština. Výchozí jazyk je angličtina.  
  
### <a name="localize-features"></a>Lokalizace funkce
 Chcete-li lokalizace funkce, budete muset nahraďte výraz, který odkazuje na řetězec v souboru lokalizované prostředky a přeložený název pevně název a popis funkce. Provedení této změny v **funkce Návrhář** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace najdete v tématu [postupy: lokalizace funkce](../sharepoint/how-to-localize-a-feature.md).  
  
 O lokalizaci vaší anglické funkce do němčina a japonština, přidejte tři položky projektu soubor prostředků do projektu: jeden pro angličtinu, jeden pro němčinu a jeden pro japonštinu. Soubory prostředků funkce nelze použít k lokalizace značek ASPX nebo kód; soubory samostatné prostředků nutných pro ně.  
  
 Po vytvoření funkci soubory prostředků, přidejte k nim přeložených řetězců. Přístup k lokalizované řetězce s výrazem v následujícím formátu:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Funkce prostředky v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vždy s názvem prostředky. Pokud vyberete jiný jazyk než neutrální jazyk, pak jazykovou verzi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] se přidá k názvu souboru prostředků. Například pokud přidáte souboru prostředků funkce neutrální jazyk (výchozí), se označuje jako *Resources.resx*. Pokud chcete přidat prostředek funkce specifické pro jazyk výběrem jazykovou verzi japonština (Japonsko), se nazývá soubor *Resources.ja JP.resx*. Názvy souborů prostředků funkce se automaticky přiřazují a nedá se změnit.  
  
 Je místní pro funkce, kterou budou přidány do oboru funkce prostředků. Chcete-li vytvořit prostředky, které můžete používat všechny funkce nebo element souboru v řešení, přidejte **globální souboru prostředků** položka projektu místo prostředek funkce souboru. **Globální souboru prostředků** položka projektu se nachází v **2010** ve složce **SharePoint** v **přidat novou položku** dialogové okno. Globální prostředky soubory nasadit do složky \Resources kořenové složce služby SharePoint.  
  
### <a name="localize-aspx-page-markup"></a>Lokalizace značek ASPX stránky
 O lokalizaci [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky, do projektu přidejte tři položky projektu soubor prostředků: jeden pro angličtinu, jeden pro němčinu a jeden pro japonštinu. Pokud nemáte lokalizace kódu kromě značku, můžete místo toho přidat globální prostředky soubory.  
  
 Zadejte název souboru prostředků jazyka výchozí. Zadejte soubory lokalizovaný prostředek se stejným názvem, spolu s jazykovou verzi pro specifický jazyk [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Například *MyAppResources.de DE.resx* pro němčinu a *MyAppResources.ja JP.resx* pro japonštinu.  
  
 Nastavte **typ nasazení** vlastnost souborů prostředků se **AppGlobalResource**. To způsobí, že soubory prostředků pro nasazení do složky App_GlobalResources, kde jsou k dispozici pro všechny stránky ASPX a ovládací prvky v řešení. App_GlobalResources složka je umístěna v C:\inetpub\wwwroot\wss\VirtualDirectories\\< číslo portu\>\App_GlobalResources.  
  
> [!NOTE]  
>  Pokud chcete použít jiný globální soubory prostředků, přesuňte je do složky položky projektu umožnit vlastnost typ nasazení a další vlastnosti specifické pro SharePoint.  
  
 Soubory prostředků značek ASPX lze také lokalizace kódu. Pokud používáte prostředky k lokalizaci kód kromě značek ASPX, ponechejte akce sestavení vlastnost nastavení pro každý soubor jako vložený prostředek způsobí prostředek pro kompilaci na satelitní sestavení. Ale pokud používáte pouze k lokalizaci značek soubory prostředků, můžete volitelně změníte akce sestavení na obsah do souboru zabránit se zkompiluje do sestavení hlavní aplikace.  
  
 Všechny vlastnosti pevně řetězce ve vašem kódu stránky a ovládací prvky ASPX nahraďte výraz v následujícím formátu:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Příklad:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Pro ASPX jako text použijte výraz v následujícím formátu:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Příklad:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Další informace najdete v tématu [postupy: lokalizace ASPX značek](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Lokalizace kódu
 Kromě lokalizace funkce řetězce a [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] značek, máte také k lokalizaci řetězce zpráv a chyba řetězce, které jsou v řešení kódu. Lokalizované informační a chybové zprávy jsou obsaženy v satelitní sestavení. Satelitní sestavení obsahovat řetězce, které jsou viditelné pro uživatele, jako například [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] zprávy text a výstup jako výjimky.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá standardní model hvězdicové rozhraní .NET Framework. Rozbočovače nebo sestavení hlavní aplikace obsahuje výchozí jazyk prostředky. Koncových nebo satelitní sestavení obsahují prostředky pro specifický jazyk. Další informace najdete v tématu [balení a nasazení prostředků](http://go.microsoft.com/fwlink/?LinkId=179280). Satelitní sestavení kompilované z prostředku (*RESX*) soubory. Když přidáte soubory prostředků pro specifický jazyk do projektu a řešení balíčku, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zkompiluje soubory prostředků do satelitní sestavení s názvem *{název projektu}.resources.dll*.  
  
 Stejně jako u značek ASPX, lokalizace kódu aplikace SharePoint přidáním položky projektu samostatný soubor prostředků do projektu; jeden pro výchozí jazyk a jeden pro jednotlivé lokalizované jazyk. Ale jak je uvedeno nahoře, pokud již máte soubory prostředků pro lokalizace značek ASPX, můžete opakovaně použít je pro lokalizace kódu. Pokud je potřeba vytvořit soubory prostředků, zadejte souboru prostředků jazyka výchozí název zvoleného s příponou *RESX* rozšíření. Název soubory lokalizovaný prostředek se stejným názvem, spolu s jazykovou verzi pro specifický jazyk [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Nastavte vlastnost Akce sestavení každého souboru prostředků na vložený prostředek a umožňují tak vytváření satelitních sestavení prostředků.  
  
 Chcete-li vytvořit satelitní sestavení, sestavení projektu a pak přidejte soubory jako další sestavení prostřednictvím **Upřesnit** kartě **návrháře balíčků**. Při přidávání sestavení, předřazení jazykovou verzi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] složku pro cestu k umístění, jako například *de-DE\\{název položky projektu}.resources.dll*. To umožňuje balíčku, který má obsahovat soubory, které mají stejný název.  
  
 Ve vašem kódu pevně řetězce nahrazeny pomocí volání <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metoda pomocí následující syntaxe:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Další informace najdete v tématu [postupy: lokalizace kódu](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Lokalizace kódu webové části
 Webové části patří funkce editor vlastní vlastnost, která obsahuje kód atributy, které používají pevně řetězce, jako je například WebDisplayName, kategorie a WebDescription. Chcete-li nahradit řetězcové hodnoty pro tyto atributy, vytvořte samostatnou třídu, která je odvozena od třídy atributu. V těchto tříd nastavte vlastnost atributu. Vlastnost atributu závisí na základní třídy. Například vlastnost WebDisplayName atributu je DisplayNameValue a vlastnost atribut WebDescription je DescriptionValue.  
  
 Odvozené třídy referenční ID řetězec ze souboru prostředků a objekt ResourceManager získat lokalizované hodnoty řetězce identifikátor. Tato hodnota se vraťte do atribut editor vlastnost.  
  
## <a name="see-also"></a>Viz také:
 [Postupy: lokalizace funkce](../sharepoint/how-to-localize-a-feature.md)   
 [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Postupy: lokalizace kódu](../sharepoint/how-to-localize-code.md)   
 [Postupy: Přidání zdrojového souboru](../sharepoint/how-to-add-a-resource-file.md)   
 [Postupy: určení lokalizovaných názvů, vlastností a oprávnění pomocí zdrojového souboru](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
