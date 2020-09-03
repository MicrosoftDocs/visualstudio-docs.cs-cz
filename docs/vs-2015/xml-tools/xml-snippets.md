---
title: Fragmenty XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669353"
---
# <a name="xml-snippets"></a>Fragmenty XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML nabízí funkci s názvem *fragmenty XML*, které umožňují rychlejší vytváření souborů XML. Můžete znovu použít fragmenty XML jejich vložením do souborů. Můžete také vygenerovat data XML na základě schématu XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Opakovaně použitelné fragmenty XML
 Editor XML obsahuje mnoho fragmentů kódu, které pokrývají některé běžné úkoly. To vám umožní snadněji vytvářet soubory XML. Například pokud jste provedli vytváření schématu XML pomocí fragmentů "element sekvence komplexního typu" a "jednoduchý typ prvku" vloží do souboru následující text XML. Pak změňte `name` hodnotu tak, aby vyhovovala vašim potřebám.

```
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Fragmenty kódu můžete vložit dvěma způsoby. Příkaz **Vložit fragment** kódu vloží fragment kódu XML na pozici kurzoru. Příkaz **Surround with** zabalí fragment XML kolem vybraného textu. Oba příkazy jsou k dispozici buď v podnabídce **IntelliSense** v nabídce **Úpravy** , nebo v místní nabídce editoru.

 Další informace naleznete v tématu [How to: use XML Fragments](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmenty XML generované schématy
 Editor XML má také možnost generovat fragment kódu XML ze schématu XML. Tato funkce umožňuje naplnit element prvky XML generovanými z informací o schématu pro daný element.

 Další informace naleznete v tématu [How to: Generate XML fragment from XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Vytvoření nových fragmentů kódu XML
 Kromě fragmentů, které jsou součástí sady [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio ve výchozím nastavení, můžete také vytvářet a používat vlastní fragmenty kódu XML.

 Další informace najdete v tématu [Postupy: vytváření fragmentů kódu XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
