---
title: Určení popisovačů souborů pro přípony názvů souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0a4f0547da10a4d519d315000a0f35a19a56287
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726250"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Určení popisovačů souborů pro přípony názvů souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existuje mnoho způsobů, jak zjistit, která zpracovává soubor, který má příponu souboru aplikace. Příkazy OpenWithList a OpenWithProgids jsou dva způsoby určení popisovačů souborů pod položkou registru pro příponu souboru.  
  
## <a name="openwithlist-verb"></a>Příkaz OpenWithList  
 Když kliknete pravým tlačítkem soubor v Průzkumníku Windows, zobrazí **otevřít** příkazu. Pokud více než jeden produkt je spojen s příponou, zobrazí se **otevřít v** podnabídka.  
  
 Různé aplikace, chcete-li spustit rozšíření pomocí klíče OpenWithList pro příponu souboru v registru HKEY_CLASSES_ROOT můžete zaregistrovat. Uvedené pod tímto klíčem pro příponu souboru aplikace se zobrazí v rámci **programy** nadpis v **otevřít v** dialogové okno. Následující příklad ukazuje zaregistrované otevřete .vcproj přípona souboru aplikace.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Ze seznamu pod HKEY_CLASSES_ROOT\Applications se klíče zadávání aplikace.  
  
 Přidáním klíčem OpenWithList deklarovat, že vaše aplikace podporuje příponu souboru i v případě, že jiná aplikace převezme vlastnictví rozšíření. To může být v budoucích verzích aplikace nebo v jiné aplikaci.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Programové identifikátory (ProgID) jsou popisný verze ID třídy, které identifikují verzi aplikace nebo objekt modelu COM. Každý společně vytvořitelný objekt by měl mít svůj vlastní identifikátor ProgID. Například VisualStudio.DTE.7.1 spustí Visual Studio .NET 2003 při spouštění VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jako vlastník projektu typu nebo typu položky projektu musíte vytvořit ProgID specifické pro verzi pro vaše příponu souboru. Tyto ProgID může být redundantní, v tom, že více než jeden identifikátor ProgID může spustit stejné aplikace. Další informace najdete v tématu [registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Aby se zabránilo duplicitě s registrací od jiných dodavatelů, použijte následujícími zásadami vytváření názvů pro souboru označeného verzí ProgID:  
  
|Přípona souboru|Verze ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Zaregistrujete různé aplikace, které jsou možné otevřít specifickou příponu souboru tak, že přidáte systémovou správou verzí ProgID jako hodnoty klíč HKEY_CLASSES_ROOT\\*\<rozšíření >* \OpenWithProgids klíč. Tento klíč registru obsahuje seznam alternativních ProgID spojené s příponou souboru. Aplikace přidružené k uvedené ProgID zobrazeny **otevřít v**_název produktu_ podnabídka. Pokud stejná aplikace je zadán v obou `OpenWithList` a `OpenWithProgids` duplicity slučuje klíče, operační systém.  
  
> [!NOTE]
>  `OpenWithProgids` Klíč se podporuje jenom ve Windows XP. Protože jinými operačními systémy Ignorovat tento klíč, nepoužívejte ho jako pouze registrace pro obslužné rutiny souborů. Pomocí tohoto klíče poskytují lepší uživatelské prostředí ve Windows XP.  
  
 Přidejte požadované ProgID jako hodnoty typu REG_NONE. Následující kód obsahuje příklad registrace ProgID pro příponu souboru (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 ProgID, zadaný jako výchozí popisovač souboru je výchozí hodnota pro příponu souboru. Pokud upravíte ProgID pro příponu souboru, dodávané spolu se předchozí verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo, které můžete provést od jiných aplikací, a potom je nutné zaregistrovat `OpenWithProgids` klíč pro vaše přípona souboru a zadejte novou ProgID v seznamu spolu s staré ProgID, kterou podporujete. Příklad:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Pokud původní ProgID má příkazy, které s ním spojená, pak tyto příkazy se také zobrazí v části **otevřít v** *název produktu* v místní nabídce.  
  
## <a name="see-also"></a>Viz také  
 [O přípony názvů souborů](../extensibility/about-file-name-extensions.md)   
 [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)

