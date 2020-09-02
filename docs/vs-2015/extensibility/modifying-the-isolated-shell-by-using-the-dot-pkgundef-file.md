---
title: Úprava izolovaného prostředí pomocí. Soubor pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538384"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Úprava izolovaného prostředí pomocí souboru .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubor. pkgundef můžete upravit tak, aby vyloučil zadané položky registru z aplikace izolovaného prostředí. Prostředí sady Visual Studio obvykle při prvním spuštění aplikace v počítači zkopíruje existující položky registru sady Visual Studio do kořenového klíče registru pro danou aplikaci. To zahrnuje všechny odkazy na aktuálně nainstalované VSPackage.  
  
 Pokud chcete vyloučit konkrétní položku registru z aplikace izolovaného prostředí, přidejte do souboru Application. pkgundef klíč balíčku následovaný položkou. Klíče a položky jsou reprezentovány stejně jako v souboru. pkgdef; To znamená, že jako [$RootKey $] nebo [$RootKey $ \\ *podklíč*] a *"entry*" =*Value*, kde je *podklíč* ovlivněný, *položka* je položka, která se má odebrat, a *hodnota* buď `""` nebo `dword:00000000` .  
  
 Chcete-li vyloučit z klíče registru více položek, stačí seznam zadat jednou a za každou položku, která má být vyloučena, potom řádek.  
  
 Pokud chcete z aplikace izolovaného prostředí vyloučit celý klíč registru, přidejte klíč do souboru Application. pkgundef, ale nezadávejte žádné položky registru pro tento klíč.  
  
 Do souboru. pkgundef můžete přidat komentáře. Jednořádkový komentář musí obsahovat dvě lomítka jako první dva znaky.  
  
 Chcete-li například odebrat příkazy **připojit k databázi** a **připojit se k obsluze r** v nabídce **nástroje** , můžete řádek odkomentovat:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 a přidejte řádek:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 do souboru. pkgundef aplikace.  
  
## <a name="see-also"></a>Viz také  
 [GUID balíčků funkcí sady Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md)
