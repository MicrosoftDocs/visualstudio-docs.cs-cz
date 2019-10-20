---
title: 'Postupy: Výběr schémat XML pro použití | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666510"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Postupy: Výběr schémat XML k použití
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML poskytuje mezipaměť schématu umístěnou v adresáři%InstallDir%\Xml\Schemas. Mezipaměť schématu obsahuje dobře známá schémata XML, která se používají pro technologii IntelliSense a ověřování dokumentů XML.

 Vlastnost dokumentu **schémata** se používá pro výběr jednoho nebo více schémat schématu definice jazyka XML (XSD), která se mají použít. Umožňuje vybrat schémata z mezipaměti schémat nebo zadat schéma, které se nenachází v mezipaměti.

 Schémata, které zadáte, se uloží do souboru uživatelských možností pro skryté řešení (. suo) společně se všemi ostatními vlastnostmi dokumentu XML. V důsledku toho není nutné znovu zadávat tyto hodnoty při příštím otevření řešení.

> [!NOTE]
> Editor se může ověřit pomocí vloženého schématu nebo schématu, na které odkazuje atribut `xsd:schemaLocation`. Další informace najdete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Výběr schématu XML z mezipaměti schématu

1. Otevřete soubor v editoru XML.

2. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

    Zobrazí se dialogové okno **schémata XML** . Dialogové okno obsahuje seznam všech schémat s příponou. xsd v mezipaměti schématu (včetně schémat, na které se odkazuje v souboru Catalog. XML), a také jakékoli schéma, které je v aktuálním řešení, otevřené v aplikaci Visual Studio, na které se odkazuje v atributu `xsd:schemaLocation`, nebo na odkaz v Vlastnost **schemas** .

3. Vyberte schémata, která chcete použít pro ověření, jedním z následujících způsobů:

   - Vyberte schéma uvedené v dialogovém okně **schémata XML** , klikněte na sloupec **použít** a pak vyberte **použít toto schéma**.

     -nebo-

   - Vyberte v dialogovém okně **schémata XML** více schémat, klikněte pravým tlačítkem myši a vyberte možnost **použít toto schéma**.

4. Klikněte na tlačítko **OK**.

    Seznam vybraných schémat se zkopíruje zpátky do vlastnosti dokumentu **schémata** .

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Přidání schématu XML do mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Klikněte na tlačítko **Přidat**.

     Otevře se dialogové okno **otevřít schéma XSD** .

3. Procházejte a vyberte schéma, které chcete přidat do mezipaměti schémat.

4. Klikněte na **otevřít**.

     Schématu přidané do mezipaměti schémat a je hodnota **použít** sloupce nastavená na **použití tohoto schématu**.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Odstranění schématu XML z mezipaměti schématu

1. V okně Vlastnosti dokumentu klikněte na tlačítko v poli **schémata** .

2. Vyberte schéma, které chcete odebrat, a klikněte na **Odebrat**.

     Schéma se odebere z mezipaměti schématu v paměti, ale neodebere se ze systému souborů.

    > [!NOTE]
    > Pokud stále máte odkaz na schéma prostřednictvím atributu `schemaLocation` nebo odpovídajícího `targetNamespace` pak **Odebrání** nebude v této situaci v důsledku automatického přidružení fungovat. V takovém případě se doporučuje označit schéma jako **Nepoužívat Vybraná schémata** ve sloupci **použít** .

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md) – [dialogové okno schémat](../xml-tools/xml-schemas-dialog-box.md) XML pro [mezipaměť schémat](../xml-tools/schema-cache.md)
