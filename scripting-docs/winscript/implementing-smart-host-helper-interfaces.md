---
title: Implementace pomocných rozhraní inteligentního hostitele | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deac5827aa38039099f1d0f5e621d473db96743d
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835599"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementace pomocných rozhraní inteligentního hostitele
Rozhraní [rozhraní idebugdocumenthelper –](../winscript/reference/idebugdocumenthelper-interface.md) značně zjednodušuje úlohu vytváření inteligentního hostitele pro aktivní ladění, protože poskytuje implementace pro mnoho rozhraní nezbytných pro inteligentní hostování.  
  
 Aby bylo možné používat inteligentního hostitele `IDebugDocumentHelper` , musí hostitelská aplikace dělat jenom tři věci:  
  
1. `CoCreate`Správce ladění procesů a k přidání aplikace do seznamu laděných aplikací použijte rozhraní [IProcessDebugManager – Interface](../winscript/reference/iprocessdebugmanager-interface.md) .  
  
2. Vytvořte pomocníka dokumentu ladění pro každý objekt skriptu pomocí metody [IProcessDebugManager –:: CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) . Ujistěte se, že je definovaný název dokumentu, nadřazený dokument, text a bloky skriptu.  
  
3. Implementujte rozhraní [rozhraní iactivescriptsitedebug –](../winscript/reference/iactivescriptsitedebug-interface.md) pro váš objekt, které implementuje rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) (které je nutné pro aktivní skriptování). Jediná netriviální metoda v `IActiveScriptSiteDebug` rozhraní jednoduše deleguje pomocníka.  
  
   Volitelně může hostitel implementovat rozhraní [rozhraní idebugdocumenthost –](../winscript/reference/idebugdocumenthost-interface.md) , pokud potřebuje větší kontrolu nad barevnou syntaxí, vytvářením kontextu dokumentu a dalšími rozšířenými funkcemi.  
  
   Hlavním omezením pomocníka pro inteligentní hostitele je, že může zpracovávat pouze dokumenty, jejichž obsah se po přidání nebo zmenšování mění (i když se dokumenty můžou rozbalit). Pro mnoho inteligentních hostitelů ale funkce, které poskytuje, je přesně to, co je potřeba.  
  
   Následující části podrobně popisují jednotlivé kroky.  
  
## <a name="create-an-application-object"></a>Vytvoření objektu aplikace  
 Předtím, než bude možné použít pomocníka inteligentního hostitele, je nutné vytvořit objekt [rozhraní IDebugApplication –](../winscript/reference/idebugapplication-interface.md) , který bude reprezentovat vaši aplikaci v ladicím programu.  
  
#### <a name="to-create-an-application-object"></a>Vytvoření objektu aplikace  
  
1. Vytvořte instanci správce procesu ladění pomocí `CoCreateInstance` .  
  
2. Zavolejte [IProcessDebugManager –:: CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3. Nastavte název aplikace pomocí [IDebugApplication –:: SetName](../winscript/reference/idebugapplication-setname.md).  
  
4. Přidejte objekt aplikace do seznamu laděných aplikací pomocí [IProcessDebugManager –:: AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Následující kód popisuje proces, ale nezahrnuje kontrolu chyb nebo jiné robustní programovací techniky.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Použití Idebugdocumenthelper –  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Použití pomocníka (minimální sekvence kroků)  
  
1. U každého hostitelského dokumentu vytvořte pomoc pomocí [IProcessDebugManager –:: CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2. Zavolejte [idebugdocumenthelper –:: init](../winscript/reference/idebugdocumenthelper-init.md) v pomocné rutině, která má název, atributy dokumentu a tak dále.  
  
3. Zavolejte [idebugdocumenthelper –:: Attach](../winscript/reference/idebugdocumenthelper-attach.md) s doplňkovou doplňkovou nápovědu pro dokument (nebo hodnotu null, pokud je dokument kořenový) pro definování pozice dokumentu ve stromu a jeho viditelnosti ladicímu programu.  
  
4. Pro definování textu dokumentu zavolejte [idebugdocumenthelper –:: AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) nebo [Idebugdocumenthelper –:: AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) . (Tyto můžou být volány víckrát, pokud se dokument stahuje přírůstkově, jako v případě prohlížeče.)  
  
5. Zavolejte [idebugdocumenthelper –::D efinescriptblock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) pro definování rozsahů pro každý blok skriptu a přidružené skriptovací stroje.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementace Iactivescriptsitedebug –  
 K implementaci [iactivescriptsitedebug –:: GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), získání pomocné rutiny odpovídající dané lokalitě a získání počátečního posunu dokumentu pro daný zdrojový kontext následujícím způsobem:  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Dále pomocí pomocné rutiny vytvořte nový kontext dokumentu pro daný posun znaku:  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 K implementaci [iactivescriptsitedebug –:: GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)jednoduše zavolejte `IDebugApplication::GetRootNode` (zděděné z [iremotedebugapplication –:: GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 K implementaci [idebugdocumenthelper –:: GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)jednoduše vraťte `IDebugApplication` původně vytvořený pomocí Správce ladění procesů.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Volitelné rozhraní Idebugdocumenthost –  
 Hostitel může poskytnout implementaci [rozhraní idebugdocumenthost –](../winscript/reference/idebugdocumenthost-interface.md) pomocí [Idebugdocumenthelper –:: SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) a dát mu tak větší kontrolu nad pomocníkem. Tady jsou některé klíčové věci, které rozhraní hostitele umožňuje:  
  
- Přidejte text pomocí [idebugdocumenthelper –:: AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) , aby hostitel nemusel ihned zadávat skutečné znaky. Pokud jsou tyto znaky skutečně požadovány, bude pomoc volat [idebugdocumenthost –:: GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) na hostiteli.  
  
- Přepsat výchozí barvy syntaxe poskytované pomocníkem. Pomoc volá [idebugdocumenthost –:: GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) , aby určila barvy pro rozsah znaků, které se vrátí k výchozí implementaci, pokud se hostitel vrátí `E_NOTIMPL` .  
  
- Poskytněte řízení neznámé pro kontexty dokumentů vytvořené pomocníkem implementací [idebugdocumenthost –:: OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). To umožňuje hostiteli přepsat funkčnost výchozí implementace kontextu dokumentu.  
  
- Zadejte název cesty v systému souborů pro dokument. Některé ladění uživatelská rozhraní toto používá, aby uživatel mohl upravovat a ukládat změny v dokumentu. [Idebugdocumenthost –:: NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) je volána pro oznamování hostitele po uložení dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ladění aktivních skriptů](../winscript/active-script-debugging-overview.md)