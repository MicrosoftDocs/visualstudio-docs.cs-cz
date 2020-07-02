---
title: 'Postupy: Výběr schémat XML pro použití'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06f9de6927d616d6cf08995c076246c8a45ec014
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815965"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Postupy: Výběr schémat XML k použití

Editor XML poskytuje mezipaměť schématu umístěnou v adresáři *%VSINSTALLDIR%\xml\Schemas* . Mezipaměť schématu obsahuje dobře známá schémata XML, která se používají pro technologii IntelliSense a ověřování dokumentů XML.

Chcete-li vybrat jedno nebo více schémat XML Schema Definition Language (XSD), použijte vlastnost dokumentu **schémata** . Můžete vybrat schémata z mezipaměti schémat nebo jinde.

Schémata, které zadáte, se uloží do souboru uživatelských možností (skryté) řešení (.* suo*) společně se všemi ostatními vlastnostmi dokumentu XML. V důsledku toho není nutné znovu zadávat tyto hodnoty při příštím otevření řešení.

> [!NOTE]
> Editor se může ověřit pomocí vloženého schématu nebo schématu, na které odkazuje `xsd:schemaLocation` atribut. Další informace najdete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Výběr schématu XML z mezipaměti schématu

1. Otevřete soubor v editoru XML.

2. V okně Vlastnosti dokumentu klikněte na pole **schémata** . Jakmile se zobrazí tlačítko pro procházení (...), klikněte na něj.

   ![Vlastnost schemas pro soubor XML](media/properties-schemas.png)

   Otevře se [dialogové okno schémata XML](xml-schemas-dialog-box.md) . Dialogové okno obsahuje seznam všech schémat s. rozšíření *XSD* v mezipaměti schématu (včetně schémat, na které se odkazuje v souboru *catalog.xml* ), a také libovolné schéma, které je v aktuálním řešení, otevřeno v aplikaci Visual Studio, odkazováno v `xsd:schemaLocation` atributu nebo odkazováno ve vlastnosti **schemas** .

3. Vyberte schémata, která chcete použít pro ověření, jedním z následujících způsobů:

   - Vyberte schéma uvedené v dialogovém okně **schémata XML** , klikněte na sloupec **použít** a pak vyberte **použít toto schéma**.

     -nebo-

   - Vyberte v dialogovém okně **schémata XML** více schémat a potom klikněte pravým tlačítkem myši a vyberte možnost **použít toto schéma**.

4. Vyberte **OK**.

   Seznam vybraných schémat se zkopíruje zpátky do vlastnosti dokumentu **schémata** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Přidání schématu XML do mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Klikněte na tlačítko **Add** (Přidat).

   Otevře se dialogové okno **otevřít schéma XSD** .

3. Procházejte a vyberte schéma, které chcete přidat do mezipaměti schémat.

4. Klikněte na **Otevřít**.

   Schémata se přidají do mezipaměti schémat a hodnota **použít** sloupec je nastavená na **použití tohoto schématu**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Odstranění schématu XML z mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Vyberte schéma, které chcete odebrat, a klikněte na **Odebrat**.

   Schéma se odebere z mezipaměti schématu v paměti, ale neodebere se ze systému souborů.

   > [!NOTE]
   > Pokud stále máte odkaz na schéma prostřednictvím `schemaLocation` atributu nebo porovnání, nebude `targetNamespace` v této situaci v důsledku **Remove** automatického přidružení fungovat. V takovém případě se doporučuje označit schéma jako **Nepoužívat Vybraná schémata** ve sloupci **použít** .

## <a name="see-also"></a>Viz také:

- [Mezipaměť schémat](../xml-tools/schema-cache.md)
- [Schéma XML – dialogové okno](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)
