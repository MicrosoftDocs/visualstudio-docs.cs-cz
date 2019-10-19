---
title: 'Postupy: Výběr schémat XML k použití'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601900"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Postupy: Výběr schémat XML k použití

Editor XML poskytuje mezipaměť schématu umístěnou v adresáři *%VSINSTALLDIR%\xml\Schemas* . Mezipaměť schématu obsahuje dobře známá schémata XML, která se používají pro technologii IntelliSense a ověřování dokumentů XML.

Chcete-li vybrat jedno nebo více schémat XML Schema Definition Language (XSD), použijte vlastnost dokumentu **schémata** . Můžete vybrat schémata z mezipaměti schémat nebo jinde.

Schémata, které zadáte, se uloží do souboru uživatelských možností (skryté) řešení (. *suo*) společně se všemi ostatními vlastnostmi dokumentu XML. V důsledku toho není nutné znovu zadávat tyto hodnoty při příštím otevření řešení.

> [!NOTE]
> Editor se může ověřit pomocí vloženého schématu nebo schématu, na které odkazuje atribut `xsd:schemaLocation`. Další informace najdete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Výběr schématu XML z mezipaměti schématu

1. Otevřete soubor v editoru XML.

2. V okně Vlastnosti dokumentu klikněte na pole **schémata** . Jakmile se zobrazí tlačítko pro procházení (...), klikněte na něj.

   ![Vlastnost schemas pro soubor XML](media/properties-schemas.png)

   Otevře se [dialogové okno schémata XML](xml-schemas-dialog-box.md) . Dialogové okno obsahuje seznam všech schémat s. rozšíření *XSD* v mezipaměti schématu (včetně schémat, na které se odkazuje v souboru *Catalog. XML* ) a také v jakémkoli schématu, které se nachází v aktuálním řešení, otevřené v aplikaci Visual Studio, na které odkazuje atribut `xsd:schemaLocation` nebo na který se odkazuje v **schématech** majetek.

3. Vyberte schémata, která chcete použít pro ověření, jedním z následujících způsobů:

   - Vyberte schéma uvedené v dialogovém okně **schémata XML** , klikněte na sloupec **použít** a pak vyberte **použít toto schéma**.

     -nebo-

   - Vyberte v dialogovém okně **schémata XML** více schémat a potom klikněte pravým tlačítkem myši a vyberte možnost **použít toto schéma**.

4. Klikněte na **tlačítko OK**.

   Seznam vybraných schémat se zkopíruje zpátky do vlastnosti dokumentu **schémata** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Přidání schématu XML do mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Klikněte na tlačítko **Přidat**.

   Otevře se dialogové okno **otevřít schéma XSD** .

3. Procházejte a vyberte schéma, které chcete přidat do mezipaměti schémat.

4. Klikněte na **otevřít**.

   Schémata se přidají do mezipaměti schémat a hodnota **použít** sloupec je nastavená na **použití tohoto schématu**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Odstranění schématu XML z mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Vyberte schéma, které chcete odebrat, a klikněte na **Odebrat**.

   Schéma se odebere z mezipaměti schématu v paměti, ale neodebere se ze systému souborů.

   > [!NOTE]
   > Pokud stále máte odkaz na schéma prostřednictvím atributu `schemaLocation` nebo odpovídajícího `targetNamespace` pak **Odebrání** nebude v této situaci v důsledku automatického přidružení fungovat. V takovém případě se doporučuje označit schéma jako **Nepoužívat Vybraná schémata** ve sloupci **použít** .

## <a name="see-also"></a>Viz také:

- [Mezipaměť schématu](../xml-tools/schema-cache.md)
- [Schéma XML – dialogové okno](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)