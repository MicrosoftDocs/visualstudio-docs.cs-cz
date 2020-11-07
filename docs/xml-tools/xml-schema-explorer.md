---
title: Průzkumník schémat XML
description: Přečtěte si o funkcích Průzkumníka schémat XML, které jsou integrovány se sadou Visual Studio a editorem XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31edea44741249c5d75a53e291c766824dc3b8ea
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351294"
---
# <a name="xml-schema-explorer"></a>Průzkumník schémat XML

**Průzkumník schémat XML** je integrovaný do Microsoft Visual Studio a editoru XML, který vám umožní pracovat s schématy XML Schema Definition Language (XSD). Když otevřete soubor schématu XML, uzel **sada schémat** se zobrazí v **Průzkumníku schémat XML**. Všechna zahrnutá, importovaná nebo Předefinovaná schémata pro cílový soubor a všechny soubory, které jsou odkazovány pomocí `include` `import` příkazu nebo, se zobrazí také v **Průzkumníku schémat XML**.

**Průzkumník schémat XML** umožňuje provést následující akce:

- Získejte rychlý přehled o sadě schémat.

- Procházení a navigace ve stromové struktuře.

- Provádění vyhledávání specifických pro klíčové slovo a schéma. Další informace najdete v tématu [hledání sady schémat](../xml-tools/searching-the-schema-set.md).

- Přidání výsledků hledání do zobrazení grafu nebo modelu obsahu

- Seřadí strom podle pořadí dokumentů, typu nebo názvu. Další informace najdete v tématu [řazení, filtrování a seskupování](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Otevřete Editor XML a přejděte do umístění kódu v souboru XSD. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).

- Vygenerujte ukázkový kód XML pro globální prvky.

**Průzkumník schémat XML** poskytuje hierarchická zobrazení sady schémat prostřednictvím stromového zobrazení. **Průzkumník schémat XML** také poskytuje hledání, filtrování, navigaci a řazení. Pro přístup k **Průzkumníku schémat XML** proveďte jednu z následujících akcí:

- Pokud jste v [zobrazení Start](../xml-tools/start-view.md), klikněte na odkaz **Průzkumník schémat XML** .

- Pokud jste v [zobrazení grafu](../xml-tools/graph-view.md) nebo v [zobrazení modelu obsahu](../xml-tools/content-model-view.md) a máte uzly ve vašem pracovním prostoru, pomocí nabídky kontext (klikněte pravým tlačítkem myši) vyberte **Průzkumník schémat XML**.

- V nabídce **zobrazení** můžete také vybrat **Průzkumníka schémat XML** .

- K **Průzkumníku schémat XML** můžete přistupovat ze souboru *. vb* , který má Visual Basic literál XML přidružený k souboru *. xsd* . Chcete-li zobrazit sadu schémat v **Průzkumníku schémat XML** , klikněte pravým tlačítkem myši na uzel XML v literálu XML nebo na import oboru názvů XML a vyberte příkaz **Zobrazit v Průzkumníku schémat** . Další informace naleznete v tématu [integrace literálů XML pomocí Průzkumníka schémat XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Stromové zobrazení
**Průzkumník schémat XML** zobrazuje předem zkompilované informace sady schémat ve stromové struktuře. Stromová struktura je uspořádána takto:

- Na nejvyšší úrovni je uzel sada schémat.

- Druhá úroveň obsahuje obory názvů.

- Třetí úroveň obsahuje soubory.

- Čtvrtá úroveň obsahuje globální uzly. To může zahrnovat prvky, skupiny, komplexní typy, jednoduché typy, atributy, skupiny atributů a `include` příkazy, a `import` `redefine` .

Následuje příklad stromové struktury:

![Průzkumník schémat XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Výběr a aktivace
Chcete-li zvýraznit a vybrat uzel, klikněte jednou v Průzkumníku schémat.

Chcete-li aktivovat uzel, poklikejte na něj nebo stiskněte klávesu **ENTER** , když je vybrán uzel.

- Aktivace uzlu otevře soubor, ve kterém je tento uzel definován (Pokud soubor již není otevřen) a vybere uzel v souboru.

- Aktivace uzlu souboru Otevře vybraný soubor (Pokud ještě není otevřený) a zvýrazní `<schema>` uzel.

- Aktivace SchemaSet nebo uzlu oboru názvů neprovede žádnou akci.

## <a name="drag-and-drop-nodes"></a>Přetažení uzlů
Můžete přetahovat globální uzly, uzly souborů a uzly oboru názvů do zobrazení návrháře XSD. Pokud je aktuální zobrazení [Úvodní zobrazení](../xml-tools/start-view.md), při přetahování uzlu na zobrazení se otevře [zobrazení grafu](../xml-tools/graph-view.md). Pokud je aktuální zobrazení [zobrazení modelu obsahu](../xml-tools/content-model-view.md) nebo zobrazení grafu, zobrazení se při zrušení uzlu do něj nezmění.

Odstraněním souborů v zobrazení přidáte všechny globální uzly v souboru do [pracovního prostoru Návrhář XSD](../xml-tools/xml-schema-designer-workspace.md). Vyřazení oborů názvů v zobrazení přidá do pracovního prostoru všechny globální uzly v oboru názvů. Pracovní prostor se sdílí mezi všemi zobrazeními.

 Nemůžete přetahovat místní uzly nebo importy.

## <a name="see-also"></a>Viz také

- [Postupy: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
