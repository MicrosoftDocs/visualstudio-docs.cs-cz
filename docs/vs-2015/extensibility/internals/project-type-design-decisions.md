---
title: Rozhodnutí o návrhu typu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704086"
---
# <a name="project-type-design-decisions"></a>Rozhodnutí týkající se návrhu typu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Před vytvořením nového typu projektu je nutné provést několik rozhodnutí o návrhu týkajících se typu projektu. Musíte rozhodnout, jaké typy položek budou vaše projekty obsahovat, jak budou zachovány soubory projektu a jaký model závazku budete používat.  
  
## <a name="project-items"></a>Položky projektu  
 Bude váš projekt používat soubory nebo abstraktní objekty? Pokud používáte soubory, budou se jednat o soubory založené na odkazech nebo adresářích? Budou soubory nebo abstraktní objekty místní nebo vzdálené?  
  
 Položky v projektu mohou být soubory, nebo mohou být více abstraktních objektů, jako jsou objekty v úložišti databáze nebo datová připojení přes Internet. Pokud jsou položky soubory, projekt může být buď odkazový, nebo projekt založený na adresáři.  
  
 V projektech založených na odkazech se položky mohou objevit ve více než jednom projektu. Samotný soubor, který položka představuje, je však umístěn pouze v jednom adresáři. V projektech založených na adresářích existují všechny položky projektu ve struktuře adresáře. Další informace naleznete v tématu [NIB: Item Management in Projects](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Místní položky jsou uloženy ve stejném počítači, ve kterém je aplikace nainstalována. Vzdálené položky mohou být uloženy na samostatném serveru v místní síti nebo jinde na internetu.  
  
## <a name="project-file-persistence"></a>Trvalost souborů projektu  
 Budou data uložená v běžných plochých souborových systémech nebo ve strukturovaném úložišti? Budou soubory otevírány pomocí standardního editoru nebo editoru specifického pro projekt?  
  
 Aby bylo možné zachovat data, většina aplikací ukládá data do souboru a pak je přečtěte zpátky, když uživatel musí informace zkontrolovat nebo změnit.  
  
 Strukturované úložiště, nazývané také složené soubory, se obvykle používá v případě, že některé objekty modelu COM (Component Object Model) potřebují ukládat trvalá data do jediného souboru. V případě strukturovaného úložiště může několik různých softwarových komponent sdílet jeden diskový soubor.  
  
 Máte několik možností, které byste měli zvážit v souvislosti s trvalými položkami v projektu. Můžete provést jednu z následujících možností:  
  
- Jednotlivé soubory uložte po změně.  
  
- Zachytit mnoho transakcí v rámci jedné operace **uložení** .  
  
- Ukládat soubory lokálně a pak je publikovat na server nebo použít jiný přístup k ukládání položek projektu, když položka představuje datové připojení ke vzdálenému objektu.  
  
  Další informace o persistenci naleznete v tématu [trvalost projektu](../../extensibility/internals/project-persistence.md) a [otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Model závazku projektu  
 Budou trvalé datové objekty otevřeny v přímém nebo transakčním režimu?  
  
 Když jsou datové objekty otevřeny v přímém režimu, změny provedené v datech jsou začleněny okamžitě nebo když uživatel soubor ručně uloží.  
  
 Když jsou datové objekty otevřeny pomocí transakčního režimu, změny jsou uloženy do dočasného umístění v paměti a nejsou potvrzeny, dokud uživatel ručně nerozhodne soubor uložit. V tomto okamžiku musí probíhat všechny změny dohromady nebo nebudou provedeny žádné změny.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: vytváření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: Správa položek v projektech](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Trvalost projektu](../../extensibility/internals/project-persistence.md)   
 [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)
