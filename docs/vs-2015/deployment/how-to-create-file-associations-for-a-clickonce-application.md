---
title: 'Postupy: vytváření přidružení souborů pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697705"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Postupy: Vytváření přidružení souborů pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je možné přidružit k jedné nebo více příponám názvů souborů, aby se aplikace spustila automaticky, když uživatel otevře soubor těchto typů. Přidání podpory přípon názvů souborů do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je jednoduché.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Vytvoření přidružení souborů pro aplikaci ClickOnce  
  
1. Vytvořte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci normálně nebo použijte existující [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci.  
  
2. Otevřete manifest aplikace pomocí textového editoru nebo editoru XML, jako je například Poznámkový blok.  
  
3. Vyhledejte `assembly` element. Další informace naleznete v tématu [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Jako podřízený `assembly` prvek elementu přidejte `fileAssociation` element. `fileAssociation`Element má čtyři atributy:  
  
   - `extension`: Přípona názvu souboru, kterou chcete přidružit k aplikaci.  
  
   - `description`: Popis typu souboru, který se zobrazí v prostředí Windows Shell.  
  
   - `progid`: Řetězec jedinečně identifikující typ souboru, který se bude označovat v registru.  
  
   - `defaultIcon`: Ikona, která se má použít pro tento typ souboru. Ikona musí být přidána jako prostředek souboru v manifestu aplikace. Další informace naleznete v tématu [How to: include a data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Příklad `file` `fileAssociation` prvků a naleznete v tématu [ \<fileAssociation> element](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Pokud chcete aplikaci přidružit více než jeden typ souboru, přidejte další `fileAssociation` prvky. Všimněte si, že `progid` atribut by měl být pro každý z nich odlišný.  
  
6. Po dokončení manifestu aplikace znovu podepište manifest. To můžete provést z příkazového řádku pomocí Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) .  
  
## <a name="see-also"></a>Viz také  
 [\<fileAssociation> Objekt](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
