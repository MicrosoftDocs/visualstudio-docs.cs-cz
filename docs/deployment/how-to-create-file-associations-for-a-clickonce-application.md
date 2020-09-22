---
title: Vytváření přidružení souborů (aplikace ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcca57415eae6480286f457755b996f22cb6507a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809778"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Postupy: vytváření přidružení souborů pro aplikaci ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je možné přidružit k jedné nebo více příponám názvů souborů, aby se aplikace spustila automaticky, když uživatel otevře soubor těchto typů. Přidání podpory přípon názvů souborů do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je jednoduché.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Vytvoření přidružení souborů pro aplikaci ClickOnce

1. Vytvořte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci normálně nebo použijte existující [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci.

2. Otevřete manifest aplikace pomocí textového editoru nebo editoru XML, jako je například Poznámkový blok.

3. Vyhledejte `assembly` element. Další informace naleznete v tématu [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md).

4. Jako podřízený `assembly` prvek elementu přidejte `fileAssociation` element. `fileAssociation`Element má čtyři atributy:

   - `extension`: Přípona názvu souboru, kterou chcete přidružit k aplikaci.

   - `description`: Popis typu souboru, který se zobrazí v prostředí Windows Shell.

   - `progid`: Řetězec jedinečně identifikující typ souboru, který se bude označovat v registru.

   - `defaultIcon`: Ikona, která se má použít pro tento typ souboru. Ikona musí být přidána jako prostředek souboru v manifestu aplikace. Další informace naleznete v tématu [How to: include a data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Příklad `file` `fileAssociation` prvků a naleznete v tématu [ \<fileAssociation> element](../deployment/fileassociation-element-clickonce-application.md).

5. Pokud chcete aplikaci přidružit více než jeden typ souboru, přidejte další `fileAssociation` prvky. Všimněte si, že `progid` atribut by měl být pro každý z nich odlišný.

6. Po dokončení manifestu aplikace znovu podepište manifest. To můžete provést z příkazového řádku pomocí *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Viz také
- [\<fileAssociation> objekt](../deployment/fileassociation-element-clickonce-application.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)