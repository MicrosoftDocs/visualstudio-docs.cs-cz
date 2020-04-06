---
title: Průvodce (. Vsz) Soubor | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703314"
---
# <a name="wizard-vsz-file"></a>Soubor průvodce (.Vsz)

Integrované vývojové prostředí (IDE) používá soubory .vsz ke spuštění průvodců. Tyto soubory .vsz obsahují informace, které rozhraní IDE používá k určení, který průvodce má volat a jaké informace mají být mu předávány.

Soubor .vsz je verze textového souboru formátu INI, který nemá žádné oddíly. Informace známé ide je uložen na začátku souboru. To poskytuje propojení mezi průvodcem, který volá rozhraní IDE, a parametry, které jsou v souboru .vsz, který má být předán rozhraní IDE. Zbytek souboru poskytuje parametry, které jsou specifické pro průvodce a které mají být shromažďovány rozhraním IDE a předány konkrétnímu průvodci.

Následující příklad ukazuje obsah souboru .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Následují části souboru .vsz.

|Část|Popis|
|----------|-----------------|
|VSWizard|Prvním parametrem v souboru je číslo verze formátu souboru šablony. Toto číslo verze musí být 6.0, 7.0, 7.1 nebo 8.0. Jiná čísla nelze spustit a způsobit chybu neplatného formátu.|
|Průvodce|Toto pole obsahuje identifikátor OLE ProgID průvodce nebo zástupce řetězce GUID identifikátoru CLSID průvodce, který je vytvořen rozhraním IDE.|
|Param|Tyto díly jsou volitelné. Můžete přidat tolik, kolik potřebujete.|

Parametry umožňují, aby soubor VSZ předal průvodci další vlastní parametry. Každá hodnota je předána jako prvek řetězce v poli variant průvodce. Další informace naleznete [v tématu Vlastní parametry](../../extensibility/internals/custom-parameters.md).

Chcete-li do souboru .vsz přidat výchozí `FALLBACK_LCID`ID národního prostředí, zadejte =xxxx, kde xxxx je ID národního prostředí, například 1033 pro angličtinu. Pokud `FALLBACK_LCID` je definován parametr, průvodce použije zadané ID záložního národního prostředí, pokud není nalezeno aktuální ID.

## <a name="see-also"></a>Viz také

- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
