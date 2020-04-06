---
title: Rozhodnutí o návrhu typu projektu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706364"
---
# <a name="project-type-design-decisions"></a>Rozhodnutí týkající se návrhu typu projektu
Před vytvořením nového typu projektu je nutné provést několik rozhodnutí o návrhu týkající se typu projektu. Musíte se rozhodnout, jaké typy položek budou projekty obsahovat, jak budou soubory projektu zachovány a jaký model závazku budete používat.

## <a name="project-items"></a>Položky projektu
 Bude projekt používat soubory nebo abstraktní objekty? Pokud používáte soubory, budou založeny na referencích nebo adresářových souborech? Budou soubory nebo abstraktní objekty místní nebo vzdálené?

 Položky v projektu mohou být soubory nebo mohou být abstraktnější objekty, jako jsou objekty v úložišti databáze nebo datová připojení přes Internet. Pokud jsou položky soubory, projekt může být na základě odkazu nebo projekt založený na adresáři.

 V projektech založených na odkazech se položky mohou zobrazit ve více než jednom projektu. Skutečný soubor, který představuje položka, je však umístěn pouze v jednom adresáři. V projektech založených na adresáři existují všechny položky projektu ve struktuře adresáře.

 Místní položky jsou uloženy ve stejném počítači, kde je aplikace nainstalována. Vzdálené položky mohou být uloženy na samostatném serveru v místní síti nebo jinde v Internetu.

## <a name="project-file-persistence"></a>Trvalost souboru projektu
 Budou data uložena ve společných plochých souborových systémech nebo ve strukturovaném úložišti? Budou soubory otevřeny pomocí standardního editoru nebo editoru specifického pro projekt?

 Chcete-li zachovat data, většina aplikací uložit data do souboru a potom si je přečíst zpět, když uživatel musí zkontrolovat nebo změnit informace.

 Strukturované úložiště, nazývané také složené soubory, se obvykle používá, když několik objektů COM (COM) potřebuje ukládat svá trvalá data do jednoho souboru. Díky strukturovanému úložišti může několik různých softwarových součástí sdílet jeden soubor na disku.

 Máte několik možností, které je třeba zvážit ohledně trvalosti pro položky v projektu. Můžete provést některou z následujících možností:

- Po změně uložte každý soubor jednotlivě.

- Zachyťte mnoho transakcí v jedné operaci **uložit.**

- Uložte soubory místně a potom publikujte na serveru nebo použijte jiný přístup k ukládání položek projektu, pokud položka představuje datové připojení ke vzdálenému objektu.

  Další informace o trvalosti naleznete v [tématu Persistence projektu](../../extensibility/internals/project-persistence.md) a [otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Model závazku projektu
 Budou trvalé datové objekty otevřeny v přímém nebo transakčním režimu?

 Při otevření datových objektů v přímém režimu jsou změny, které byly provedeny v datech, začleněny okamžitě nebo když uživatel soubor uloží ručně.

 Při otevření datových objektů pomocí transakčního režimu jsou změny uloženy do dočasného umístění v paměti a nejsou potvrzeny, dokud se uživatel ručně nerozhodne soubor uložit. V tomto okamžiku musí všechny změny dojít společně nebo žádné změny budou provedeny.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Trvalost projektu](../../extensibility/internals/project-persistence.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)
