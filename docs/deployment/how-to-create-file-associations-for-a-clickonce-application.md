---
title: 'Postupy: vytváření přidružení souborů pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25d8d12b8ad49b40309845def60964c13a3da708
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919387"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Postupy: vytváření přidružení souborů pro aplikaci ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace může být přidružený jeden nebo více přípon souborů, tak, aby aplikaci spustit automaticky, když uživatel otevře soubor z těchto typů. Přidání podpory přípony názvu souboru [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací je jednoduché.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Chcete-li vytvořit přidružení souborů pro aplikaci ClickOnce  
  
1. Vytvoření [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace za normálních okolností nebo použít stávající [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.  
  
2. Otevření manifestu aplikace se textovém editoru nebo editoru XML, jako je například Poznámkový blok.  
  
3. Najít `assembly` elementu. Další informace najdete v tématu [ClickOnce – manifest aplikace](../deployment/clickonce-application-manifest.md).  
  
4. Jako podřízený objekt `assembly` element, přidejte `fileAssociation` elementu. `fileAssociation` Element má čtyři atributy:  
  
   - `extension`: Příponu názvu souboru, kterou chcete přiřadit k aplikaci.  
  
   - `description`: Popis typu souboru, který se zobrazí v prostředí Windows.  
  
   - `progid`: Řetězec, který jednoznačně identifikuje typ souboru k označení v registru.  
  
   - `defaultIcon`: Ikonu pro tento typ souboru. Ikona je nutné přidat jako soubor prostředků v manifestu aplikace. Další informace najdete v tématu [postupy: zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Příkladem `file` a `fileAssociation` prvky, naleznete v tématu [ \<fileAssociation > Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Pokud chcete přidružit více než jeden typ souboru aplikace, přidejte další `fileAssociation` elementy. Všimněte si, `progid` atribut by měl být různé pro jednotlivé.  
  
6. Jakmile budete hotovi s manifestem aplikace, znovu podepište manifest. Můžete to provést z příkazového řádku pomocí *Mage.exe*.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Viz také:  
 [\<fileAssociation > – element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce – manifest aplikace](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)