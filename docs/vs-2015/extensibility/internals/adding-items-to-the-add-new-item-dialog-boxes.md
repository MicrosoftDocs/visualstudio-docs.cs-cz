---
title: Přidávání položek do přidání nové položky v dialogových oknech | Dokumentace Microsoftu
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
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca9ae7d9e4f0ffc031d2dc8db3e940c9b844c57e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778550"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Přidávání položek do dialogových oken Přidat novou položku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proces přidávání položek do **přidat novou položku** spustí dialogové okno s klíči registru. Jak je znázorněno v následující položky registru, obsahuje cestu a název adresáře, ve které položky k dispozici v části AddItemTemplates **přidat novou položku** jsou umístěny dialogové okno.  
  
> [!NOTE]
>  Tabulka ihned po segmentu kódu obsahuje další informace o položku registru.  
  
 V této části se nachází v části [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 První identifikátor GUID je identifikátor CLSID projektech tohoto typu; druhý identifikátor GUID označuje typ registrované projektu pro přidání položek šablony.  
  
 \\\1 \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} {C061DB26-5833-11D2-96F5-000000000000}  
  
 @="#6"  
  
 "TemplatesDir"="\<cestu instalace sady Visual Studio SDK\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|Název|Typ|Data (ze souboru .rgs)|Popis|  
|----------|----------|-----------------------------|-----------------|  
|@ (Výchozí)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID prostředku pro **přidat položku** šablony.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Cesta položky projektu zobrazí v dialogovém okně pro **přidat novou položku** průvodce.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|Určuje pořadí řazení v uzlu stromu soubory zobrazené v **přidat novou položku** dialogové okno.|  
  
> [!NOTE]
>  Identifikátory GUID pro typy projektů jazyka Visual C# a Visual Basic jsou následující:[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Adresář uvedený TemplateDirs, což je % TEMPLATE_PATH%\SomeProjectItems, je uzel na levé straně **přidat novou položku** dialog box stromu. Další prvky ve stromu jsou založeny na podadresáře v tomto kořenovém adresáři. Položky v pravém podokně jsou k dispozici mají být přidány do projektu soubory **přidat novou položku** dialogové okno.  
  
 Obvykle se tato složka obsahovat soubory šablon pro váš projekt, například šablonu HTML nebo soubor .cpp a všechny soubory pro spuštění průvodců. Pokud chcete řídit, jak jsou zobrazeny položky, můžete použít také souborů .vsdir pro lokalizaci názvy adresářů a ikony. Lokalizovaný řetězec je popisek, který se zobrazí v dialogovém okně, které představuje tento uzel ve stromu dialogového okna Přidat novou položku.  
  
 Však není nutné mít všechno v jednom souboru .vsdir. Můžete mít jednu projektový soubor pro každou položku v adresáři. Další informace najdete v tématu [průvodce (. Soubor vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) a [popisu adresáře šablon (. Soubory VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  .Vsdir soubory v adresářích šablony jsou volitelné. Pokud chcete pouze umístit prvek projektu v adresáři a zobrazit je v **přidat novou položku** dialogovém okně můžete umístit tento soubor v adresáři šablony zadaných v příkazu TemplatesDir. Soubor se pak zobrazí v pravém podokně **přidat novou položku** dialogové okno pro daný projekt. Ale pokud chcete zobrazit lokalizované titulek pro soubor nebo ikonu, musí obsahovat jeden nebo více souborů .vsdir v adresáři šablony.  
  
## <a name="grouping-project-items"></a>Seskupení položek projektu  
 Pokud budete chtít obsahují šablony skupiny do složek v **přidat novou položku** dialogové okno pole stromu, musí mít podadresářích v kořenovém adresáři šablony položky v nich. Když **přidat novou položku** dialogové okno se zobrazí uživatelům, budou také naleznete v tématu podsložky a mít možnost vybrat elementy projektu z nich.  
  
 Priorita řazení v segmentu kódu určuje, kde se tento adresář šablony vytvoří ve stromové struktuře vzhledem k další prvky uzlu stromu. Pro **přidat novou položku** dialogové okno, prioritu řazení je vše, co musí obsahovat tak, aby vaše položky se zobrazí ve správném umístění v dialogovém okně.  
  
 Můžete také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> rozhraní k filtrování, co se zobrazí **přidat novou položku** dialogové okno. Prostřednictvím implementace tohoto rozhraní, můžete nastavit jednu šablonu adresáře na disku, který obsahuje, například 50 Průvodce šablony a souborů. Tímto způsobem může mít různé typy projektů s 20 souborů, které patří do jednoho projektu typu, jiné 30 souborů, které patří k jinému typu projektu a všechny soubory, které jsou k dispozici v obecné typu projektu. Tímto způsobem, v závislosti na tom, který projekt se vytvoří šablonu, můžete zobrazit jinou sadu souborů šablon.  
  
 Například v projektu jazyka Visual Basic, bude pravděpodobně webové projekty a projekty klienta. Webové formuláře nejsou užitečné položky pro přidání do projektu klienta a modelu windows forms nejsou užitečné položky pro přidání do projektu webového serveru. Proto můžete vytvořit jeden adresář šablon, která obsahuje všechny soubory pro oba typy projektu. Pak pomocí implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, skryjete položky, které nebude zobrazovat na základě typu projektu nebo nastavení projektu na projekt.  
  
## <a name="filtering-project-items"></a>Filtrování položek projektu  
 `IVsFilterAddProjectItemDlg2` poskytuje pro filtrování ve stromu (levé podokno) a soubory projektu (pravé podokno) prvků následujícími způsoby:  
  
- Lokalizované názvy (titulky zobrazují v dialogovém okně, které jsou obsaženy v souboru .vsdir) poskytované `IVsFilterAddProjectItemDlg`.  
  
- Skutečné názvy souborů a složek na disku (Nelokalizováno – žádný soubor .vsdir) poskytované `IVsFilterAddProjectItemDlg`.  
  
- Podle kategorie, poskytuje `IVsFilterAddProjectItemDlg2`.  
  
  Chcete-li filtrovat podle kategorie, zadejte řetězec kategorie pro položky v souboru .vsdir, jako je například "Webový formulář" nebo "Klienta item" v jazyce Visual Basic. Kódu dialogového okna pak načte kategorie klasifikace z projektový soubor a předává je na vás. Tyto informace můžete předat do vaší implementace `IVsFilterAddProjectItemDlg2` k filtrování **přidat novou položku** dialogové okno podle kategorií. Můžete také filtrovat položky pro webové stránky nebo jako klient případy aplikaci Win32. Kromě toho můžete identifikovat [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] položky označené jako Microsoft Foundation Classes (MFC) nebo položky aktivní šablony knihovny (ATL). Při určování tyto položky můžete systém projektu tak, aby systém je možné filtrovat podle kategorií a klasifikací definovat své vlastní klasifikace.  
  
  Pokud implementujete tuto funkci filtru, nemají mapování tabulky všechny položky, který by měl být skrytý. Můžete jednoduše klasifikovat položky do typů a vložit klasifikace projektový soubor nebo soubory. Potom můžete skrýt, některá z položek, které mají určité klasifikace prostřednictvím implementace rozhraní. Tímto způsobem můžete vytvořit položky v **přidat novou položku** dynamické dialogové okno pole na základě stavu v rámci projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Identifikátory CatID pro objekty, které se obvykle používají k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Přidání projektu a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Popis šablony adresáře (. Soubory VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

