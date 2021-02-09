---
title: Funkce IntelliSense v editoru XML
description: Přečtěte si o funkcích IntelliSense v editoru XML v aplikaci Visual Studio a o tom, jak je můžete použít s XML Schema Definition Language (XSD) a XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 330dbdfb6d6db8d33a2b8ea3caa7e1a840d84dd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874896"
---
# <a name="xml-editor-intellisense-features"></a>Funkce IntelliSense editoru XML

Editor XML poskytuje úplné funkce technologie IntelliSense srovnatelné s jinými jazykovými editory, které jsou součástí sady Visual Studio. V této části se dozvíte, jak můžete používat technologii IntelliSense s dokumenty XSD (XML Schema Definition Language) a XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense v dokumentu XSD

Po přiřazení schématu k vašemu dokumentu získáte rozevírací seznam očekávaných prvků pokaždé, když zadáte `"<"` nebo kliknete na tlačítko **Zobrazit seznam členů objektu** na panelu nástrojů editoru XML.

![Tlačítko seznamu členů zobrazovaného objektu](media/display-object-member-list-xml.png)

Informace o tom, jak přidružit schémata k dokumentům XML, naleznete v tématu [ověření dokumentu XML](../xml-tools/xml-document-validation.md).

Při psaní prostoru zevnitř počáteční značky získáte také rozevírací seznam obsahující všechny atributy, které lze přidat do aktuálního prvku.

Když zadáte `"="` hodnotu atributu nebo počáteční uvozovku pro hodnotu, získáte také seznam možných hodnot pro tento atribut. Hodnoty jsou poskytnuty pouze v případě, že schéma poskytuje výčtové hodnoty prostřednictvím `xsd:enumeration` omezujících vlastností nebo pokud je atribut `Boolean` typu. Seznam známých kódů jazyků technologie IntelliSense je také k dispozici pro `xml:lang` nebo všechny `simpleType` , které jsou odvozeny z `xsd:language` . `targetNamespace`Pro deklarace oboru názvů je k dispozici seznam známých hodnot technologie IntelliSense.

K dispozici je také seznam možných hodnot technologie IntelliSense, pokud zadáte `">"` , aby se zavřela počáteční značka, je-li element `simpleType` . Chování pro prvky je podobné chování atributů popsaných v předchozím odstavci.

Popisy se zobrazí také na těchto seznamech IntelliSense na `xsd:annotation` základě `xsd:documentation` informací uvedených v přidruženém schématu.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense v dokumentu XSLT

Po přidání pojmenované šablony nebo atributu do dokumentu XSLT lze pomocí technologie IntelliSense vložit následující:

- Názvy sady atributů.

- Režimy šablon.

- Názvy šablon.

- Názvy parametrů pro daný režim.

- Názvy parametrů pro danou pojmenovanou šablonu.

Další informace naleznete v tématu [Návod: použití XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) .

## <a name="auto-completion"></a>Automatické dokončování

Editor XML také usnadňuje úpravy XML vyplněním požadované syntaxe XML za vás. Pokud například zadáte následující počáteční značku:

`<book>`

Editor XML vyplní koncovou značku a umístí kurzor za počáteční značku. Toto je příklad tohoto příkladu ("&#124;" poznámkou pozice kurzoru):

`<book>`&#124;`</book>`

Vzhledem k tomu, že hodnoty atributu musí mít vždy uvozovky, editor XML vyplní uvozovky. Pokud například zadáte následující:

`<book title=`

Editor XML přidá uvozovky a umístí kurzor mezi uvozovky:

`<book title="`&#124;`"`

Podobně editor XML také automaticky vloží následující syntaxi XML za vás:

- Konec instrukcí pro zpracování:  `?>`

- Konec bloku CDATA: `]]>`

- Konec komentáře: `-->`

- Konec deklarace DTD: `>`

Editor XML má také možnost vložit deklaraci oboru názvů, pokud vyberete kvalifikovaný atribut oboru názvů nebo atribut ze seznamu technologie IntelliSense a obor názvů pro tento element nebo atribut ještě není v oboru.

Například pokud vyberete `e:Book` prvek ze seznamu technologie IntelliSense, kde je předpona svázána s `http://books` oborem názvů, který nebyl deklarován v dokumentu, vloží editor XML požadovanou deklaraci oboru názvů. Následuje výsledný text XML:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Spárování složených závorek

Editor XML nabízí zvýraznění složených závorek, které poskytuje okamžitou zpětnou vazbu na prvky, které jste právě zavřeli. Můžete také použít klávesovou zkratku (**CTRL** + **]**) a přeskočit jednu složenou závorku k párové závorce.

Editor XML provede následující položky:

- Porovnání počátečních a koncových značek.

- Libovolný pár \<" or "> lomených závorek.

- Začátek a konec komentářů

- Začátek a konec instrukcí pro zpracování.

- Začátek a konec bloků CDATA.

- Začátek a konec deklarací DTD

- Otevírání a zavírání uvozovek u atributů.

## <a name="modify-the-intellisense-options"></a>Úprava možností IntelliSense

Funkce IntelliSense a automatické dokončování jsou ve výchozím nastavení povoleny. Můžete to však změnit úpravou   >  nastavení **možností** nástroje.

Část **Automatické vložení** stránky **různé** určuje následující chování:

|Název|Description|
|-|-----------------|
|Zavřít značky|Vloží uzavírací značky pro nové prvky.|
|Uvozovky atributů|Vloží uvozovky hodnot atributů při zadání nového názvu atributu.|
|Jiné značky|Dokončí komentáře, CDATA, DOCTYPE, pokyny pro zpracování a další deklarace značek.|

### <a name="to-change-the-auto-completion-behavior"></a>Změna chování automatického dokončování

1. V nabídce **nástroje** vyberte **možnost možnosti** .

2. Rozbalte položku **textový editor**, rozbalte položku **XML** a vyberte možnost **různé**.

3. Proveďte jakékoli změny v části **Automatické vložení** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
- [Pomocí technologie IntelliSense](../ide/using-intellisense.md)
- [Návod: Používání IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md)
