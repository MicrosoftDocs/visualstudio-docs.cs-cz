---
title: Vytvoření modelu připojení obchodních dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68940d6e48f1f3a3e51017e1cc838976735de104
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930203"
---
# <a name="create-a-business-data-connectivity-model"></a>Vytvoření modelu připojení obchodních dat
  Můžete vytvořit obchodní Data připojení (BDC) model nebo přizpůsobit existující model služby BDC pomocí sady Visual Studio. Každý projekt služby SharePoint může obsahovat pouze jeden model. Další informace najdete v tématu [integraci obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Vytvořit nový model
 Vytvořit nový model, vytvořte **Model Připojení obchodních dat** projektu nebo přidat **Model Připojení obchodních dat** položku **prázdný projekt SharePoint**.  
  
> [!NOTE]  
>  Musíte mít [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] v počítači nainstalována.  
  
 Visual Studio přidá složku do projektu. Tato složka obsahuje název, který zadáte pro **Model Připojení obchodních dat** položky v **přidat novou položku** dialogové okno. Pokud vytvoříte nový **Model Připojení obchodních dat** názvy složky projektu, Visual Studio **BdcModel1**.  
  
 Visual Studio přidá následující soubory do nové složky:  
  
|Soubor|Popis|  
|----------|-----------------|  
|Soubor definice modelu|Obsahuje kód XML, který definuje entity, metody, řádek obchodní (LOB) systémové objekty a další metadata, která popisuje model.<br /><br /> Upravit metadata v tomto souboru pomocí návrháři služby BDC **služby BDC Explorer**, **podrobnosti metody služby BDC** okně a **vlastnosti** okna.|  
|Soubor kódu služby entity|Obsahuje metody, které načítají, aktualizovat a odstranit instance výchozí entity.|  
  
 K definování vlastností entity, upravte soubor kódu entity. Další informace naleznete v tématu [jak: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Získat, aktualizovat a odstraňovat instancí entity, přidejte kód do souboru kód služby entity. Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Při kompilaci projektu sady Visual Studio vytváří sestavení. Zajištění Nepřidávejte další položky pro projekt, který je přidání kódu k sestavení projektu (například: **sekvenčního pracovního postupu** položky nebo **webové části** položky). Kód pro tuto položku se nespustí, když nasadíte řešení, protože balíček řešení není zkopírujte sestavení do globální mezipaměti sestavení.  Balíček řešení nasadí do databáze služby BDC v Sharepointu pouze sestavení.  
  
> [!NOTE]  
>  Sestavení sady Visual Studio kopíruje do obou umístěních v místním počítači, při ladění projektu.  
  
## <a name="add-an-existing-model"></a>Přidat existující model
 Můžete importovat modelu, který byl vytvořen pomocí jiných nástrojů, jako je SharePoint designeru. Můžete se rozhodnout pro import existujícího modelu do projektu v následujících situacích:  
  
- Přizpůsobení modelu, který už je nasazená do farmy serverů SharePoint.  
  
- Balení a nasazení existujícího modelu do více Sharepointové serverové farmy.  
  
  V obou případech systémům LOB definované v modelu, který importujete neovlivní a budou fungovat podle očekávání. K přidání existujícího modelu do projektu služby SharePoint, pomocí sady Visual Studio **přidat existující položku** dialogové okno. Další informace najdete v tématu [postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
  Můžete přidat systému LOB typ sestavení rozhraní .NET Framework pro importovaný model tak, že vyberete možnost v **objekt LobSystem sestavení .NET přidat**. To umožňuje psát vlastní kód a definují metadata pro importovaný model pomocí návrháře.  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)|Ukazuje, jak vytvořit nový model služby BDC.|  
|[Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Ukazuje, jak importovat existující model do projektu služby SharePoint.|  
|[Postupy: určení lokalizovaných názvů, vlastností a oprávnění pomocí zdrojového souboru](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Popisuje, jak poskytnout řetězce, které jsou sloučeny metadat modelu, když model je využívána webové části nebo webové stránky.|  
|[Postupy: zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Ukazuje, jak zahrnutí vlastního sestavení ve funkci.|  
  
 
