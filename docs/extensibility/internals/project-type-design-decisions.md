---
title: Rozhodnutí o návrhu typu projektu | Microsoft Docs
description: Přečtěte si informace o položce, trvalosti souborů projektu a závazku pro rozhodování o návrhu nástroje, který je třeba provést před rozšiřováním sady Visual Studio vytvořením nového typu projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab29fbe79b474aa7b640faf81de812b7571de861
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877794"
---
# <a name="project-type-design-decisions"></a>Rozhodnutí týkající se návrhu typu projektu
Před vytvořením nového typu projektu je nutné provést několik rozhodnutí o návrhu týkajících se typu projektu. Musíte rozhodnout, jaké typy položek budou vaše projekty obsahovat, jak budou zachovány soubory projektu a jaký model závazku budete používat.

## <a name="project-items"></a>Položky projektu
 Bude váš projekt používat soubory nebo abstraktní objekty? Pokud používáte soubory, budou se jednat o soubory založené na odkazech nebo adresářích? Budou soubory nebo abstraktní objekty místní nebo vzdálené?

 Položky v projektu mohou být soubory, nebo mohou být více abstraktních objektů, jako jsou objekty v úložišti databáze nebo datová připojení přes Internet. Pokud jsou položky soubory, projekt může být buď odkazový, nebo projekt založený na adresáři.

 V projektech založených na odkazech se položky mohou objevit ve více než jednom projektu. Samotný soubor, který položka představuje, je však umístěn pouze v jednom adresáři. V projektech založených na adresářích existují všechny položky projektu ve struktuře adresáře.

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
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Trvalost projektu](../../extensibility/internals/project-persistence.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)
