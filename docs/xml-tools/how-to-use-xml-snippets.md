---
title: Jak používat fragmenty kódu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4758fbebea12b014f92bed59e851210509cdbb9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573125"
---
# <a name="how-to-use-xml-snippets"></a>Postupy: použití XML fragmenty kódu

Pomocí následujících příkazů v místní nabídce editoru XML můžete vyvolat fragmenty kódu XML. **Vložit fragment** příkaz vloží fragment kódu XML na pozici kurzoru. **Příkazu Obklopit s** příkaz zabalí fragment kódu XML kolem vybraný text. Každý fragment kódu XML určil typy fragment kódu. Typy fragment kódu určit, zda je k dispozici v tomto fragmentu kódu **Vložit fragment** příkaz, **příkazu Obklopit s** příkaz nebo obojí.

Po tomto fragmentu kódu XML se přidal do editoru, všechna upravitelné pole v tomto fragmentu kódu jsou vyznačené na žlutý a kurzor je nastavený na první upravitelné pole.

## <a name="insert-snippet"></a>Vložit fragment kódu

Následující postupy popisují, jak získat přístup **Vložit fragment** příkaz.

> [!NOTE]
> **Vložit fragment** příkaz je také k dispozici prostřednictvím klávesové zkratky (**Ctrl**+**tisíc**, pak **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Chcete-li vložit fragmenty kódu z místní nabídky

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Klikněte pravým tlačítkem a vyberte **Vložit fragment**.

   Zobrazí se seznam dostupných fragmenty kódu XML.

3. Vyberte fragment ze seznamu pomocí myši nebo zadáním názvu fragment kódu a stiskněte **kartě** nebo **Enter**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Chcete-li vložit fragmenty kódu pomocí nabídky IntelliSense

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Z **upravit** nabídky, přejděte na příkaz **IntelliSense**a potom vyberte **Vložit fragment**.

   Zobrazí se seznam dostupných fragmenty kódu XML.

3. Vyberte fragment ze seznamu pomocí myši nebo zadáním názvu fragment kódu a stiskněte **kartě** nebo **Enter**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Chcete-li vložit fragmenty kódu pomocí seznamu dokončení word IntelliSense

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Začněte psát fragment kódu XML, který chcete přidat do souboru. Pokud je zapnutá funkce automatického dokončování, se zobrazí seznam dokončení slov IntelliSense. Pokud se nezobrazí, stiskněte klávesu **Ctrl**+**místo** aktivovat.

3. Vyberte ze seznamu dokončení word fragment kódu XML.

4. Stiskněte klávesu **kartě**, **kartě** k vyvolání fragment kódu XML.

> [!NOTE]
> Můžou nastat případy při získání vyvolání není fragment kódu XML. Například pokud se pokusíte vložit `xs:complexType` element uvnitř `xs:element` uzlu editoru negeneruje fragmentu kódu XML. Když `xs:complexType` element se používá v `xs:element` uzlu, nejsou žádné povinné atributy dílčí prvky, takže editoru nemá žádná data k vložení.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Chcete-li vložit fragmenty kódu pomocí názvu odkazu

1. Umístěte kurzor na místo, kam chcete vložit fragment kódu XML.

2. Typ `<` v podokně editor.

3. Stiskněte klávesu **Esc** zavřete seznamu dokončení word IntelliSense.

4. Zadejte název zástupce fragment kódu a stiskněte klávesu **kartě** k vyvolání fragment kódu XML.

## <a name="surround-with"></a>Obklopit fragmentem

Následující postupy popisují, jak získat přístup **příkazu Obklopit s** příkaz.

> [!NOTE]
> **Příkazu Obklopit s** příkaz je také k dispozici prostřednictvím klávesové zkratky (**Ctrl**+**tisíc**, pak **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Použití příkazu Obklopit s z místní nabídky

1. Vyberte text, který má obklopit v editoru XML.

2. Klikněte pravým tlačítkem a vyberte **příkazu Obklopit s**.

   Zobrazí se seznam dostupných okolí s fragmenty kódu XML.

3. Vyberte fragment ze seznamu pomocí myši nebo zadáním názvu fragment kódu a stiskněte **kartě** nebo **Enter**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Použití příkazu Obklopit s z nabídky IntelliSense

1. Vyberte text, který má obklopit v editoru XML.

2. Z **upravit** nabídky, přejděte na příkaz **IntelliSense**a potom vyberte **příkazu Obklopit s**.

   Zobrazí se seznam dostupných okolí s fragmenty kódu XML.

3. Vyberte fragment ze seznamu pomocí myši nebo zadáním názvu fragment kódu a stiskněte **kartě** nebo **Enter**.

## <a name="use-xml-snippets"></a>Použití fragmenty kódu XML

Jakmile vyberete fragmentu kódu XML, se automaticky vloží text fragmentu kódu na pozici kurzoru. Jsou vyznačené všechna upravitelné pole v tomto fragmentu kódu a je automaticky vybrána první upravitelné pole. Aktuálně vybrané pole je zabalená.

Pokud je vybraná pole, můžete zadat novou hodnotu pro pole. Stisknutím **kartě** procházení upravitelné pole fragmentu; stiskněte **Shift**+**kartě** přepínání mezi je v obráceném pořadí. Kliknutím na pole umístí kurzor v poli a dvakrát klikněte na pole vybere. Pokud pole zvýrazní, popisek mohou být zobrazeny, nabídky popis pole.

Pouze první instance dané pole lze upravit. Když toto pole je zvýrazní, jsou uvedeny další instance tohoto pole. Když změníte hodnotu upravitelné pole, je toto pole změnit všude, kde se používá v tomto fragmentu kódu.

Stisknutím **Enter** nebo **Esc** zruší úpravy pole a vrátí editoru normální.

Výchozí barvy pro upravovat kód fragment kódu pole lze změnit úpravou **pole fragmentu kódu** nastavení v **písma a barev** podokně **možnosti** dialogové okno. Další informace najdete v tématu [postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu XML](../xml-tools/xml-snippets.md)
- [Postupy: generování fragmentu kódu XML z schématu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Postupy: vytvoření fragmenty kódu XML](../xml-tools/how-to-create-xml-snippets.md)