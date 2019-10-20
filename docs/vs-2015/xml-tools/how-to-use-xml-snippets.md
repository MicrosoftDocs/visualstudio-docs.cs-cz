---
title: 'Postupy: používání fragmentů kódu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656265"
---
# <a name="how-to-use-xml-snippets"></a>Postupy: používání fragmentů kódu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu XML lze vyvolat pomocí následujících dvou příkazů v místní nabídce editoru XML. Příkaz **Vložit fragment** kódu vloží fragment kódu XML na pozici kurzoru. Příkaz **Surround with** zabalí fragment XML kolem vybraného textu. Každý fragment kódu XML má určené typy fragmentů. Typy fragmentů určují, zda je fragment kódu k dispozici v příkazu **Vložit fragment** , příkaz **obklopit pomocí** příkazu nebo obojí.

 Po přidání fragmentu kódu XML do editoru jsou všechna upravitelná pole ve fragmentu zvýrazněna žlutě a kurzor je umístěn v prvním upravitelném poli.

## <a name="insert-snippet"></a>Vložit fragment
 Následující postupy popisují, jak získat přístup k příkazu **Vložit fragment** .

> [!NOTE]
> Příkaz **Vložit fragment** je také k dispozici prostřednictvím klávesové zkratky (CTRL + K a pak CTRL + X).

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Vložení fragmentů z místní nabídky

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Klikněte pravým tlačítkem a vyberte **Vložit fragment**.

     Zobrazí se seznam dostupných fragmentů kódu XML.

3. Vyberte ze seznamu fragment kódu pomocí myši nebo zadejte název fragmentu a stiskněte klávesu TAB nebo ENTER.

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Vložení fragmentů pomocí nabídky technologie IntelliSense

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. V nabídce **Úpravy** přejděte na **IntelliSense**a pak vyberte **Vložit fragment**.

     Zobrazí se seznam dostupných fragmentů kódu XML.

3. Vyberte fragment ze seznamu pomocí myši nebo zadáním názvu fragmentu a stisknutím klávesy TAB nebo ENTER.

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Vložení fragmentů do seznamu slov kompletního slova IntelliSense

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Začněte psát fragment kódu XML, který chcete přidat do souboru. Je-li automatické dokončování zapnuté, zobrazí se seznam slov kompletních funkcí IntelliSense. Pokud se nezobrazí, aktivujte ji stisknutím kombinace kláves CTRL + MEZERNÍK.

3. Vyberte fragment kódu XML ze seznamu kompletních slov.

4. Stiskněte tabulátor, TAB a volejte fragment kódu XML.

> [!NOTE]
> Můžou nastat případy, kdy fragment kódu XML není vyvolán. Například pokud se pokusíte vložit prvek `xs:complexType` do uzlu `xs:element`, Editor negeneruje fragment kódu XML. Pokud je `xs:complexType` element použit uvnitř uzlu `xs:element`, nejsou vyžadovány žádné atributy ani dílčí prvky, takže Editor neobsahuje žádná data, která by bylo možné vložit.

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Vložení fragmentů kódu pomocí názvu zástupce

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Zadejte `<` v podokně editoru.

3. Stisknutím klávesy ESC zavřete seznam slov kompletních aplikací IntelliSense.

4. Zadejte název zástupce fragmentu a stisknutím klávesy TAB volejte fragment XML.

## <a name="surround-with"></a>Obklopit
 Následující postupy popisují, jak získat přístup k příkazu **uzavřít pomocí** příkazu.

> [!NOTE]
> Příkaz **obklopit pomocí** je dostupný taky prostřednictvím klávesové zkratky (CTRL + K a pak CTRL + S).

#### <a name="to-use-surround-with-from-the-context-menu"></a>Použití Surround with v místní nabídce

1. Vyberte text, který má být ohraničen v editoru XML.

2. Klikněte pravým tlačítkem a vyberte možnost **obklopit**.

     Zobrazí se seznam dostupných ohraničení s fragmenty kódu XML.

3. Vyberte ze seznamu fragment kódu pomocí myši nebo zadejte název fragmentu a stiskněte klávesu TAB nebo ENTER.

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Použití funkce Surround with v nabídce technologie IntelliSense

1. Vyberte text, který má být ohraničen v editoru XML.

2. V nabídce **Úpravy** přejděte na **IntelliSense**a pak vyberte **obklopit s**.

     Zobrazí se seznam dostupných ohraničení s fragmenty kódu XML.

3. Vyberte ze seznamu fragment kódu pomocí myši nebo zadejte název fragmentu a stiskněte klávesu TAB nebo ENTER.

## <a name="using-xml-snippets"></a>Používání fragmentů XML
 Po výběru fragmentu kódu XML je text fragmentu kódu vložen automaticky na pozici kurzoru. Všechna upravitelná pole ve fragmentu kódu jsou zvýrazněna a první upravitelná pole je vybráno automaticky. Aktuálně vybrané pole je zabaleno.

 Když je vybráno pole, můžete zadat novou hodnotu pole. Stisknutí klávesy TAB pomocí upravitelných polí fragmentu; stisknutí SHIFT + TAB cyklicky v opačném pořadí. Kliknutím na pole umístíte kurzor do pole a dvakrát kliknete na pole, které vyberete. Když je zvýrazněno pole, může se zobrazit popisek, který nabízí popis pole.

 Upravovat se dá jenom první instance daného pole. Když je toto pole zvýrazněno, ostatní instance tohoto pole jsou poznačené. Když změníte hodnotu upravitelného pole, toto pole se změní všude, kde se používá ve fragmentu.

 Stisknutí klávesy ENTER nebo ESC zruší úpravy polí a vrátí Editor do normálního režimu.

 Výchozí barvy pro upravitelná pole fragmentu kódu lze změnit úpravou nastavení pole fragment kódu v podokně **písma a barvy** v dialogovém okně **Možnosti** . Další informace najdete v tématu [Postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také
 [Fragmenty kódu XML](../xml-tools/xml-snippets.md) [Postupy: generování fragmentu XML ze schématu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md) [Postupy: vytváření fragmentů kódu XML](../xml-tools/how-to-create-xml-snippets.md)
