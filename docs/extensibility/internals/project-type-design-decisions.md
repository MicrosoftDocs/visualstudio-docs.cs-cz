---
title: Rozhodnutí o návrhu typu projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bd6d2188b46093c5bfe18f9cabe985a953c000f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869480"
---
# <a name="project-type-design-decisions"></a>Rozhodnutí týkající se návrhu typu projektu
Než vytvoříte nový typ projektu, je nutné provést několik rozhodnutí o návrhu týkající se vašeho typu projektu. Musíte se rozhodnout, jaké typy položek, které bude obsahovat vaše projekty, jak se soubory projektu trvalý a jaké závazku modelu, které použijete.  
  
## <a name="project-items"></a>Položky projektu  
 Váš projekt bude používat soubory nebo abstraktní objekty? Pokud používáte soubory, budou se soubory na základě odkazu nebo na adresář? Jsou soubory nebo abstraktní objekty probíhající být místní nebo vzdálený?  
  
 Položky v projektu mohou být soubory, nebo můžou být více abstraktní objekty, jako jsou objekty v databázi úložiště nebo datového připojení přes Internet. Pokud položky jsou soubory, může být projektu odkaz na základě nebo projektu založeného na adresář.  
  
 Položky můžete v projektech na základě odkazu, se zobrazí ve více než jeden projekt. Ale skutečný soubor, který představuje položku se nachází v jednom adresáři pouze. V projektech adresář existovat všechny položky projektu do struktury adresářů.  
  
 Místní položky, které jsou uložené ve stejném počítači, kde je nainstalována aplikace. Vzdálené položky může být uloženy na jiném serveru v místní síti nebo jinde v síti Internet.  
  
## <a name="project-file-persistence"></a>Trvalost souborů projektu  
 Data se uloží v běžné systémy plochého souboru, nebo strukturované úložiště? Soubory se otevřou pomocí standardního editoru nebo editoru specifické pro projekt?  
  
 Většina aplikací uchovávat svá data, uložit svá data v souboru a poté číst zpět, když uživatel musí zkontrolovat nebo změnit informace.  
  
 Strukturované úložiště, také nazývané složené soubory se obvykle používá při několika objekty modelu COM (Component Object) vyžadují pro ukládání trvalých dat v jednom souboru. Pomocí strukturovaného úložiště můžete několik různých softwarových komponent sdílet soubor jeden disk.  
  
 Máte několik možností, jak ke zvážení při výběru trvalosti pro položky ve vašem projektu. Můžete provést některou z následujících možností:  
  
- Každý soubor byl změněn jednotlivě uložte.  
  
- Zachycení velký počet transakcí v jediném **Uložit** operace.  
  
- Uložit soubory místně a potom publikovat na server nebo použít jiný přístup k uložení položek projektu, pokud položka představuje datové připojení ke vzdálenému objektu.  
  
  Další informace o trvalosti najdete v tématu [trvalost projektu](../../extensibility/internals/project-persistence.md) a [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Model projektu závazku  
 Trvalá data objekty se otevřou v s přímým přístupem nebo počet zrušených zpracovaných režimu?  
  
 Když datových objektů jsou otevřené v režimu přímého, změny, které byly provedené v datech jsou začleněny okamžitě, nebo když uživatel ručně uloží soubor.  
  
 Při otevření datové objekty pomocí transakčního režimu, změny se uloží do dočasného umístění v paměti a nejsou potvrzeny, dokud uživatel ručně vybere možnost uložení souboru. V tu chvíli musí dohromady všech změnách nebo nebudou provedeny žádné změny.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Trvalost projektu](../../extensibility/internals/project-persistence.md)   
 [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)