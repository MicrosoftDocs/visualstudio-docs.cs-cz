---
title: Nainstalovat rozhraní pro testování částí třetích stran | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660516"
---
# <a name="install-third-party-unit-test-frameworks"></a>Instalace systémů testování částí od třetích stran
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Průzkumník testů sady Visual Studio může spustit libovolné prostředí pro testování částí, které vyvinulo rozhraní adaptéru pro Průzkumníka. Instalační program rozhraní nainstaluje binární soubory a přidá šablony projektů sady Visual Studio pro jazyky, které podporuje. Při vytváření projektu se šablonou je rozhraní registrováno v Průzkumníku testů. Řešení sady Visual Studio může obsahovat projekty testování částí, které používají různá rozhraní a cílí na různé jazyky. Průzkumník testů je spouští všechny.

 **Požadavky**

- Visual Studio Enterprise Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Získání rozhraní třetích stran
 Můžete stáhnout a nainstalovat mnoho rozhraní pro testování částí třetích stran pomocí Správce rozšíření sady Visual Studio nebo z galerie sady Visual Studio na webu MSDN. Rozhraní lze také stáhnout z jiných webů, jako je například web rozhraní.

### <a name="installing-from-visual-studio"></a>Instalace ze sady Visual Studio

1. Zvolte **nástroje** v nabídce Standard a pak zvolte **rozšíření a aktualizace**.

2. Rozbalte položku **online**, **Galerie sady Visual Studio**, **nástroje**. Vyberte možnost **testování**.

3. V seznamu vyhledejte rozhraní.

4. Vyberte architekturu a zvolte **Stáhnout**.

   Další informace najdete v tématu [vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Instalace z webu
 Pokud znáte rozhraní, na které vás zajímáte, postupujte takto:

1. Otevřete [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Do pole **Najít** zadejte název rozhraní.

3. Vyberte architekturu v seznamu výsledků a přejděte na stránku galerie sady Visual Studio pro daný nástroj.

   Chcete-li procházet seznam platforem spolu s dalšími testovacími nástroji:

4. Otevřete [Visual Studio Marketplace](https://marketplace.visualstudio.com).

5. Klikněte na tlačítko **Procházet**.

6. V seznamu **kategorie** rozbalte uzel **nástroje** a pak zvolte možnost **testování**.

7. Vyberte architekturu v seznamu výsledků a přejděte na stránku galerie sady Visual Studio pro daný nástroj.

## <a name="see-also"></a>Viz také
 [Testy jednotek kódu](../test/unit-test-your-code.md)
