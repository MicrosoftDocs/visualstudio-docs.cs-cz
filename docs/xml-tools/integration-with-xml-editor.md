---
title: Integrace návrháře schématu XML s editorem XML
description: Přečtěte si o integraci mezi návrhářem schémat XML a editorem XML a jak se změny provedené v jednom projeví v druhé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe1bfcd422dbfc5f010ae7819e2fccbeafb8227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934621"
---
# <a name="integration-with-xml-editor"></a>Integrace s editorem XML

Návrhář schématu XML je integrován s editorem XML. Pokud upravíte soubor XSD v editoru XML, změna se projeví v [Průzkumníku schémat XML](../xml-tools/xml-schema-explorer.md). Pokud máte [zobrazení grafu](../xml-tools/graph-view.md) nebo [zobrazení modelu obsahu](../xml-tools/content-model-view.md) otevřené, bude tato změna také odrážet. Můžete přecházet mezi návrhářem schémat XML a editorem XML následujícími způsoby:

- V editoru XML klikněte pravým tlačítkem myši na uzel a vyberte možnost **Zobrazit v Průzkumníku schémat XML**.

- V zobrazení grafu a v **Průzkumníku schémat XML** poklikejte na uzel, nebo klikněte pravým tlačítkem myši na uzel a vyberte **Zobrazit kód**. V zobrazení modelu obsahu klikněte pravým tlačítkem myši na uzel a vyberte možnost **Zobrazit kód**.

Následující snímek obrazovky ukazuje schéma XML otevřené v **Průzkumníku schémat XML**. **Průzkumník schémat XML** zobrazí sadu schémat ve stromovém zobrazení. Editor XML zobrazuje textové zobrazení uzlu, který je aktuálně aktivní v **Průzkumníku schémat XML**.

![Snímek obrazovky projektu sady Visual Studio znázorňující uzel XML v podokně editoru XML a stromové zobrazení sady schémat v podokně Průzkumník schémat XML.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Někdy je užitečné zobrazit kód v editoru XML a grafickém návrháři vedle sebe. Chcete-li zobrazit oba soubory současně, klikněte pravým tlačítkem myši kdekoli v editoru XML a vyberte možnost **Návrhář zobrazení**. V nabídce aplikace Visual Studio v systému Windows vyberte možnost **Nová vodorovná (nebo svislá) skupina karet**.

![Snímek projektu sady Visual Studio znázorňující podokno návrháře zobrazení, podokno editoru XML a podokno Průzkumník schémat XML.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Viz také

- [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)
