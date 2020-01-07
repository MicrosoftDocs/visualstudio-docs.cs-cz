---
title: Fragmenty kódu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592318"
---
# <a name="xml-snippets"></a>Fragmenty kódu XML

Editor XML nabízí funkci s názvem *fragmenty XML*, které umožňují rychlejší vytváření souborů XML. Můžete znovu použít fragmenty XML jejich vložením do souborů. Můžete také vygenerovat data XML na základě schématu XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Opakovaně použitelné fragmenty XML

Editor XML obsahuje mnoho fragmentů kódu, které pokrývají některé běžné úkoly. To vám umožní snadněji vytvářet soubory XML. Například pokud jste provedli vytváření schématu XML pomocí fragmentů "element sekvence komplexního typu" a "jednoduchý typ prvku" vloží do souboru následující text XML. Pak změňte hodnotu `name` tak, aby vyhovovala vašim potřebám.

```xml
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

Fragmenty kódu můžete vložit dvěma způsoby. Příkaz **Vložit fragment** kódu vloží fragment kódu XML na pozici kurzoru. Příkaz **Surround with** zabalí fragment XML kolem vybraného textu. Oba příkazy jsou k dispozici buď z podnabídky **IntelliSense** v nabídce **Úpravy** , nebo z místní nabídky v editoru.

Další informace naleznete v tématu [How to: use XML Fragments](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmenty XML generované schématy

Editor XML má také možnost generovat fragment kódu XML ze schématu XML. Tato funkce umožňuje naplnit element prvky XML generovanými z informací o schématu pro daný element. Další informace naleznete v tématu [How to: Generate XML fragment from XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Vytvoření nových fragmentů kódu XML

Kromě fragmentů, které jsou součástí sady Visual Studio ve výchozím nastavení, můžete také vytvářet a používat vlastní fragmenty kódu XML. Další informace najdete v tématu [Postupy: vytváření fragmentů kódu XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu v aplikaci Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)
