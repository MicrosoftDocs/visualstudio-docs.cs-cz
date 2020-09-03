---
title: Kdy vytvořit typy projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5bc2bacb53973bd552b983b742e4f9e68fe31b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687702"
---
# <a name="when-to-create-project-types"></a>Kdy vytvořit typy projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvořením nového typu projektu získáte základ pro přizpůsobení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pro uživatele. Vytvoření nového typu projektu však není vyžadováno pro všechna [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] přizpůsobení. Následující pokyny vám pomohou určit, zda je pro váš scénář požadován nový typ projektu.  
  
## <a name="create-a-new-project-type"></a>Vytvořit nový typ projektu  
 Typ projektu musíte vytvořit, pokud chcete přizpůsobit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aby fungoval v jednom nebo několika následujících způsobech:  
  
- Zapojit se do sestavení, nasazení, konfigurací a správy zdrojového kódu.  
  
- Nabízí podporu ladění.  
  
- Zobrazit položky projektu v **Průzkumník řešení**.  
  
- Použijte dialogové okno **Otevřít projekt** nebo **Nový projekt** .  
  
- Podporuje vnořování projektů.  
  
## <a name="extend-an-existing-project-type"></a>Rozšíří existující typ projektu  
 Můžete chtít vytvořit nový typ projektu, který může být použit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] následujícími způsoby pro úpravu nebo rozšiřování chování existujícího typu projektu, například úpravou procesu sestavení pro [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekty:  
  
- Pracujte s více soubory jako s jednou jednotkou.  
  
- Zobrazí jeden soubor jako hierarchii dílčích položek.  
  
- Zobrazí kontext příkazu kolem editorů.  
  
- Zobrazit kontext služby pro editory.  
  
## <a name="use-an-existing-project-type"></a>Použít existující typ projektu  
 Vytvoření nového projektu někdy není nutné. V následující tabulce jsou uvedeny úlohy, které nemusíte vytvořit typ projektu pro.  
  
|Úkol|Popis|  
|----------|-----------------|  
|Zpracování příkazů|Všechny VSPackage můžou zpracovávat příkazy.|  
|Sestavování editoru|Vlastní editory je možné zaregistrovat. Další informace najdete v tématu [okna a editory dokumentů](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Vlastnící okna|Můžete vytvořit okna nástrojů i dokumentu bez přidání nového typu projektu.|  
|Vystavení vlastností v okno Vlastnosti|Všechny objekty mohou vystavit vlastnosti.|  
  
## <a name="create-a-project-subtype"></a>Vytvoření podtypu projektu  
 Můžete použít podtypy projektu pro rozšiřování spravovaného typu projektu bez nutnosti vytvořit nový typ projektu. Podtypy projektů používají agregaci COM k rozšiřování spravovaných projektů napsaných v Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Pomocí agregace modelu COM můžete znovu použít většinu implementace spravovaného projektového systému a ještě přizpůsobit konkrétní scénář prostřednictvím agregace a používání podpůrných rozhraní. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Viz také  
 [Okna a editory dokumentů](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Kontrolní seznam: vytváření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
