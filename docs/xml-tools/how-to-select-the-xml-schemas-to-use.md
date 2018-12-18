---
title: 'Postupy: Výběr schémat XML pro použití'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a04075c0625eb7b4dc899a4e183588b96eb7eadd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872236"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Postupy: Výběr schémat XML pro použití

XML Editor poskytuje nachází v mezipaměti schématu *%InstallDir%\Xml\Schemas* adresáře. Mezipaměti schématu obsahuje dobře známými schématy XML, které slouží k ověření dokumentu technologie IntelliSense a XML.

**Schémata** vlastnost dokumentu slouží k výběru jedné nebo více schématu definice jazyk (XSD) schématu XML používat. Umožní vám vybrat schémata z mezipaměti schémat nebo změnu schématu, který se nenachází v mezipaměti.

Schémata zadáte se ukládají do skrytého souboru s možností řešení uživatele (. *suo*), společně s další XML vlastnosti dokumentu. V důsledku toho není nutné znovu zadat tyto hodnoty při příštím otevření řešení.

> [!NOTE]
> V editoru můžete ověřit pomocí vložené schéma nebo schéma. odkazuje `xsd:schemaLocation` atribut. Další informace najdete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Chcete-li vybrat schématu XML z mezipaměti schémat

1. Otevření souboru v editoru XML.

2. V okně Vlastnosti dokumentu, klepněte na tlačítko **schémata** pole.

    **Schémat XML** se zobrazí dialogové okno. Dialogové okno obsahuje všechna schémata pomocí. *xsd* rozšíření v mezipaměti schématu (včetně schémata odkazuje *catalog.xml* souboru) a také jakékoli schéma, které se v aktuálním řešení, otevřete v sadě Visual Studio, odkazuje v `xsd:schemaLocation` atribut, nebo odkazuje **schémata** vlastnost.

3. Výběr schémat pro účely ověření pomocí jedné z následujících akcí:

   - Vyberte schéma uvedené v **schémat XML** dialogového okna, klikněte na tlačítko **použití** sloupec a pak vyberte **použít tohle schéma**.

     -nebo-

   - Výběr více schémat, které jsou uvedeny v **schémat XML** dialogového okna, klikněte pravým tlačítkem a vyberte **použít tohle schéma**.

4. Klikněte na tlačítko **OK**.

    Seznam vybraná schémata zkopírována zpět **schémata** vlastnost dokumentu.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Přidat do mezipaměti schématu schématu XML

1.  V okně Vlastnosti dokumentu, klepněte na tlačítko **schémata** pole.

2.  Klikněte na tlačítko **přidat**.

     Tím se otevře **otevřít schéma XSD** dialogového okna.

3.  Vyhledejte a vyberte schémata pro přidání do mezipaměti schématu.

4.  Klikněte na tlačítko **otevřít**.

     Schémata přidané do schématu do mezipaměti a je **použití** nastavena na hodnotu sloupce **použít tohle schéma**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Chcete-li odstranit schématu XML z mezipaměti schémat

1.  V okně Vlastnosti dokumentu, klepněte na tlačítko **schémata** pole.

2.  Vyberte schéma odebrat a potom klikněte na **odebrat**.

     Schéma se odebere z mezipaměti schémat v paměti, ale neodebere se ze systému souborů.

    > [!NOTE]
    > Pokud stále máte odkaz na schéma prostřednictvím `schemaLocation` atribut nebo odpovídající `targetNamespace` pak **odebrat** nebude fungovat v této situaci kvůli automatické přidružení. V tomto případě se doporučuje, abyste označili schématu jako **nepoužívat vybraná schémata** v **použít** sloupce.

## <a name="see-also"></a>Viz také:

- [Mezipaměti schémat](../xml-tools/schema-cache.md)
- [Dialogové okno schémata XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)