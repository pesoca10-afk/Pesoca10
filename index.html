import { useState, useRef, useEffect, useCallback } from "react";
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer } from "recharts";

const SPORTS = ["Fútbol","Atletismo","Natación","Ciclismo","Gimnasia","Boxeo","Tenis","Baloncesto","Halterofilia","CrossFit","Rugby","Volleyball","Otro"];
const ICONS = {"Fútbol":"⚽","Atletismo":"🏃","Natación":"🏊","Ciclismo":"🚴","Gimnasia":"🤸","Boxeo":"🥊","Tenis":"🎾","Baloncesto":"🏀","Halterofilia":"🏋️","CrossFit":"💪","Rugby":"🏉","Volleyball":"🏐","Otro":"🏅"};
const MFIELDS = [
  {k:"weight",l:"Peso",u:"kg",g:"general"},
  {k:"neck",l:"Cuello",u:"cm",g:"superior"},
  {k:"shoulders",l:"Hombros",u:"cm",g:"superior"},
  {k:"chest",l:"Pecho/Tórax",u:"cm",g:"superior"},
  {k:"armR",l:"Brazo relajado",u:"cm",g:"superior"},
  {k:"armF",l:"Brazo contraído",u:"cm",g:"superior"},
  {k:"forearm",l:"Antebrazo",u:"cm",g:"superior"},
  {k:"waist",l:"Cintura",u:"cm",g:"central"},
  {k:"abdomen",l:"Abdomen",u:"cm",g:"central"},
  {k:"hip",l:"Cadera",u:"cm",g:"central"},
  {k:"thigh",l:"Muslo",u:"cm",g:"inferior"},
  {k:"calf",l:"Pantorrilla",u:"cm",g:"inferior"},
];
const GROUPS = {general:"⚖️ General",superior:"💪 Tren Superior",central:"📐 Zona Central",inferior:"🦵 Tren Inferior"};
const DAYS = ["Lunes","Martes","Miércoles","Jueves","Viernes","Sábado","Domingo"];
const MEALS = ["Desayuno","Media mañana","Almuerzo","Merienda","Cena","Post-entreno"];
const TABS = [
  {id:"meas",l:"📏",full:"Mediciones"},
  {id:"charts",l:"📊",full:"Evolución"},
  {id:"nutrition",l:"🥗",full:"Nutrición"},
  {id:"training",l:"🏋️",full:"Entreno"},
  {id:"reminders",l:"🗓️",full:"Fechas"},
  {id:"chat",l:"🤖",full:"Chat IA"},
];

function uid(){ return Date.now().toString(36)+Math.random().toString(36).slice(2); }
function today(){ return new Date().toISOString().split("T")[0]; }
function fdate(iso){ return new Date(iso).toLocaleDateString("es-AR",{day:"2-digit",month:"short",year:"numeric"}); }
function calcFat(g,h,neck,waist,hip){
  if(!h||!neck||!waist) return null;
  try{
    if(g==="M") return Math.round((495/(1.0324-0.19077*Math.log10(waist-neck)+0.15456*Math.log10(h))-450)*10)/10;
    if(!hip) return null;
    return Math.round((495/(1.29579-0.35004*Math.log10(waist+hip-neck)+0.22100*Math.log10(h))-450)*10)/10;
  }catch{return null;}
}
function calcIMC(w,h){ if(!w||!h) return null; return Math.round((w/Math.pow(h/100,2))*10)/10; }

const C = {
  bg:"#060c0a", sidebar:"#080f0c", card:"rgba(255,255,255,0.04)",
  border:"rgba(255,255,255,0.08)", accent:"#00d4a8", accent2:"#0099ee",
  text:"#e0f0ea", muted:"#4a8a78", danger:"#ff6b6b", warn:"#ffd93d"
};
const grad = `linear-gradient(135deg,${C.accent},${C.accent2})`;
const Btn = ({onClick,children,primary,danger,small,disabled,full}) => (
  <button onClick={onClick} disabled={disabled} style={{
    padding: small?"7px 13px":"10px 18px", borderRadius:10, border:"none",
    fontWeight:700, fontSize:small?12:13, cursor:disabled?"default":"pointer",
    transition:"all 0.15s", width:full?"100%":"auto", opacity:disabled?0.5:1,
    background: danger?"rgba(255,107,107,0.12)":primary?grad:"rgba(255,255,255,0.06)",
    color: danger?C.danger:primary?"#fff":C.muted,
  }}>{children}</button>
);

function Input({label,value,onChange,type="text",placeholder="",rows}){
  const s={width:"100%",background:"rgba(255,255,255,0.05)",border:`1px solid ${C.border}`,borderRadius:10,padding:"10px 13px",color:C.text,fontSize:14,outline:"none",fontFamily:"inherit",boxSizing:"border-box"};
  return(
    <div style={{marginBottom:12}}>
      {label&&<label style={{fontSize:12,color:C.muted,display:"block",marginBottom:5}}>{label}</label>}
      {rows?<textarea value={value} onChange={e=>onChange(e.target.value)} placeholder={placeholder} rows={rows} style={{...s,resize:"vertical"}}/>
           :<input type={type} value={value} onChange={e=>onChange(e.target.value)} placeholder={placeholder} style={s}/>}
    </div>
  );
}
function Sel({label,value,onChange,options}){
  return(
    <div style={{marginBottom:12}}>
      {label&&<label style={{fontSize:12,color:C.muted,display:"block",marginBottom:5}}>{label}</label>}
      <select value={value} onChange={e=>onChange(e.target.value)} style={{width:"100%",background:C.sidebar,border:`1px solid ${C.border}`,borderRadius:10,padding:"10px 13px",color:C.text,fontSize:14,outline:"none"}}>
        {options.map(o=>typeof o==="string"?<option key={o} value={o}>{o}</option>:<option key={o.v} value={o.v}>{o.l}</option>)}
      </select>
    </div>
  );
}
function Modal({title,onClose,children,wide}){
  return(
    <div style={{position:"fixed",inset:0,background:"rgba(0,0,0,0.82)",zIndex:300,display:"flex",alignItems:"center",justifyContent:"center",padding:12,overflowY:"auto"}}>
      <div style={{background:"#0a1a15",border:`1.5px solid ${C.accent}44`,borderRadius:20,padding:24,width:"100%",maxWidth:wide?680:440,maxHeight:"92vh",overflowY:"auto"}}>
        <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:18}}>
          <h2 style={{margin:0,fontSize:17,fontWeight:800,color:C.text}}>{title}</h2>
          <button onClick={onClose} style={{background:"none",border:"none",color:C.muted,fontSize:22,cursor:"pointer",lineHeight:1}}>✕</button>
        </div>
        {children}
      </div>
    </div>
  );
}

// ── ATHLETE FORM ──
function AthleteForm({existing,onSave,onClose}){
  const [f,setF]=useState(existing||{name:"",sport:"Otro",gender:"M",age:"",height:"",goal:"",notes:""});
  const s=(k,v)=>setF(p=>({...p,[k]:v}));
  return(
    <Modal title={existing?"Editar atleta":"Nuevo atleta"} onClose={onClose}>
      <Input label="Nombre completo *" value={f.name} onChange={v=>s("name",v)} placeholder="Ej: Milagros Fernández"/>
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10}}>
        <Sel label="Género" value={f.gender} onChange={v=>s("gender",v)} options={[{v:"M",l:"♂ Masculino"},{v:"F",l:"♀ Femenino"}]}/>
        <Sel label="Deporte" value={f.sport} onChange={v=>s("sport",v)} options={SPORTS}/>
        <Input label="Edad" value={f.age} onChange={v=>s("age",v)} type="number" placeholder="Ej: 24"/>
        <Input label="Altura (cm)" value={f.height} onChange={v=>s("height",v)} type="number" placeholder="Ej: 165"/>
      </div>
      <Input label="Objetivo principal" value={f.goal} onChange={v=>s("goal",v)} placeholder="Ej: Bajar 5kg, mejorar resistencia..."/>
      <Input label="Notas / Alergias / Restricciones" value={f.notes} onChange={v=>s("notes",v)} placeholder="Alergias, lesiones, intolerancias..." rows={2}/>
      <div style={{display:"flex",gap:10,marginTop:8}}>
        <Btn onClick={onClose}>Cancelar</Btn>
        <button onClick={()=>f.name.trim()&&onSave(f)} disabled={!f.name.trim()} style={{flex:2,padding:"11px",borderRadius:10,border:"none",background:f.name.trim()?grad:"rgba(255,255,255,0.05)",color:f.name.trim()?"#fff":"#555",fontSize:14,fontWeight:700,cursor:f.name.trim()?"pointer":"default"}}>
          {existing?"Guardar cambios ✓":"Crear atleta ✓"}
        </button>
      </div>
    </Modal>
  );
}

// ── MEASUREMENT FORM ──
function MeasForm({athlete,existing,onSave,onClose}){
  const [date,setDate]=useState(existing?.date||today());
  const [flds,setFlds]=useState(()=>{const o={};MFIELDS.forEach(f=>{o[f.k]=existing?.[f.k]||""});return o;});
  const set=(k,v)=>setFlds(p=>({...p,[k]:v}));
  const fat=calcFat(athlete.gender||"M",parseFloat(athlete.height),parseFloat(flds.neck),parseFloat(flds.waist),parseFloat(flds.hip));
  const imc=calcIMC(parseFloat(flds.weight),parseFloat(athlete.height));
  const lean=fat&&flds.weight?Math.round(parseFloat(flds.weight)*(1-fat/100)*10)/10:null;
  const fmass=fat&&flds.weight?Math.round(parseFloat(flds.weight)*fat/100*10)/10:null;
  return(
    <Modal title={existing?"Editar medición":"Nueva medición"} onClose={onClose} wide>
      <p style={{margin:"0 0 14px",fontSize:13,color:C.muted}}>Atleta: <strong style={{color:C.text}}>{athlete.name}</strong></p>
      <Input label="📅 Fecha" value={date} onChange={setDate} type="date"/>
      {Object.entries(GROUPS).map(([gk,gl])=>(
        <div key={gk} style={{marginBottom:16}}>
          <div style={{fontSize:11,fontWeight:700,color:C.accent,textTransform:"uppercase",letterSpacing:"1px",marginBottom:8}}>{gl}</div>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8}}>
            {MFIELDS.filter(f=>f.g===gk).map(f=>(
              <div key={f.k}>
                <label style={{fontSize:11,color:C.muted,display:"block",marginBottom:3}}>{f.l} ({f.u})</label>
                <input type="number" step="0.1" value={flds[f.k]} onChange={e=>set(f.k,e.target.value)} placeholder="—"
                  style={{width:"100%",background:"rgba(255,255,255,0.05)",border:`1px solid ${C.border}`,borderRadius:9,padding:"9px 11px",color:C.text,fontSize:14,outline:"none",boxSizing:"border-box"}}/>
              </div>
            ))}
          </div>
        </div>
      ))}
      {(fat||imc)&&(
        <div style={{background:`${C.accent}12`,border:`1px solid ${C.accent}33`,borderRadius:14,padding:14,marginBottom:16}}>
          <div style={{fontSize:11,fontWeight:700,color:C.accent,marginBottom:10,textTransform:"uppercase",letterSpacing:"1px"}}>⚡ Calculado automáticamente</div>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8}}>
            {[["% Grasa (Navy)",fat?fat+"%":"—",C.danger],["IMC",imc||"—",C.warn],["Masa magra",lean?lean+" kg":"—",C.accent],["Masa grasa",fmass?fmass+" kg":"—","#f97316"]].map(([l,v,col])=>(
              <div key={l} style={{background:"rgba(0,0,0,0.25)",borderRadius:10,padding:"9px 12px"}}>
                <div style={{fontSize:10,color:C.muted}}>{l}</div>
                <div style={{fontSize:17,fontWeight:800,color:col,marginTop:2}}>{v}</div>
              </div>
            ))}
          </div>
        </div>
      )}
      <div style={{display:"flex",gap:10}}>
        <Btn onClick={onClose}>Cancelar</Btn>
        <button onClick={()=>onSave({id:existing?.id||uid(),date,...flds,fatPercent:fat,imc,leanMass:lean})}
          style={{flex:2,padding:"11px",borderRadius:10,border:"none",background:grad,color:"#fff",fontSize:14,fontWeight:700,cursor:"pointer"}}>
          Guardar medición ✓
        </button>
      </div>
    </Modal>
  );
}

// ── MEAS LIST ──
function MeasList({athlete,measurements,onNew,onEdit,onDelete}){
  const sorted=[...measurements].sort((a,b)=>new Date(b.date)-new Date(a.date));
  return(
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14}}>
        <span style={{fontSize:13,color:C.muted}}>{measurements.length} medición{measurements.length!==1?"es":""}</span>
        <Btn primary onClick={onNew}>+ Nueva medición</Btn>
      </div>
      {sorted.length===0?(
        <div style={{textAlign:"center",padding:"30px",color:C.muted}}><div style={{fontSize:36,marginBottom:8}}>📏</div><div>Cargá la primera medición</div></div>
      ):sorted.map((m,idx)=>{
        const prev=sorted[idx+1]; const isLast=idx===0;
        return(
          <div key={m.id} style={{background:C.card,border:`1px solid ${isLast?"rgba(0,212,168,0.35)":C.border}`,borderRadius:14,padding:14,marginBottom:10}}>
            <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:10}}>
              <span style={{fontWeight:700,color:C.text,fontSize:14}}>📅 {fdate(m.date)}</span>
              {isLast&&<span style={{background:`${C.accent}18`,border:`1px solid ${C.accent}44`,borderRadius:20,padding:"2px 10px",fontSize:11,color:C.accent,fontWeight:700}}>Última</span>}
            </div>
            <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(95px,1fr))",gap:7,marginBottom:10}}>
              {m.weight&&<SB l="Peso" v={m.weight+" kg"} prev={prev?.weight}/>}
              {m.fatPercent&&<SB l="% Grasa" v={m.fatPercent+"%"} prev={prev?.fatPercent} lower/>}
              {m.leanMass&&<SB l="Masa magra" v={m.leanMass+" kg"} prev={prev?.leanMass}/>}
              {m.imc&&<SB l="IMC" v={m.imc}/>}
              {MFIELDS.filter(f=>f.k!=="weight"&&m[f.k]).map(f=><SB key={f.k} l={f.l} v={m[f.k]+" cm"}/>)}
            </div>
            <div style={{display:"flex",gap:8}}>
              <Btn small onClick={()=>onEdit(m)}>✏️ Editar</Btn>
              <Btn small danger onClick={()=>confirm("¿Eliminar medición?")&&onDelete(m.id)}>🗑️</Btn>
            </div>
          </div>
        );
      })}
    </div>
  );
}
function SB({l,v,prev,lower}){
  const cur=parseFloat(v),pv=parseFloat(prev);
  const diff=prev&&!isNaN(cur)&&!isNaN(pv)?Math.round((cur-pv)*10)/10:null;
  const up=diff!==null?(lower?diff<0:diff>0):null;
  return(
    <div style={{background:"rgba(0,0,0,0.2)",borderRadius:10,padding:"8px 10px"}}>
      <div style={{fontSize:10,color:C.muted,marginBottom:2}}>{l}</div>
      <div style={{fontSize:14,fontWeight:700,color:C.text}}>{v}</div>
      {diff!==null&&<div style={{fontSize:11,color:up?C.accent:C.danger,marginTop:1}}>{diff>0?"▲":"▼"} {Math.abs(diff)}</div>}
    </div>
  );
}

// ── CHARTS ──
function Charts({measurements}){
  const [active,setActive]=useState(["weight","fatPercent"]);
  const metrics=[
    {k:"weight",l:"Peso (kg)",c:C.accent},{k:"fatPercent",l:"% Grasa",c:C.danger},
    {k:"leanMass",l:"Masa Magra",c:"#4ecdc4"},{k:"waist",l:"Cintura",c:C.warn},
    {k:"hip",l:"Cadera",c:"#a78bfa"},{k:"chest",l:"Pecho",c:"#f97316"},
  ];
  const data=[...measurements].sort((a,b)=>new Date(a.date)-new Date(b.date)).map(m=>({
    date:new Date(m.date).toLocaleDateString("es-AR",{day:"2-digit",month:"short"}),
    weight:m.weight?+m.weight:undefined,fatPercent:m.fatPercent||undefined,
    leanMass:m.leanMass||undefined,waist:m.waist?+m.waist:undefined,
    hip:m.hip?+m.hip:undefined,chest:m.chest?+m.chest:undefined,
  }));
  if(measurements.length<2) return(
    <div style={{textAlign:"center",padding:"40px 20px",color:C.muted}}>
      <div style={{fontSize:40,marginBottom:10}}>📊</div>
      <div>Necesitás al menos 2 mediciones para ver la evolución</div>
    </div>
  );
  return(
    <div>
      <div style={{display:"flex",flexWrap:"wrap",gap:7,marginBottom:16}}>
        {metrics.map(m=>(
          <button key={m.k} onClick={()=>setActive(p=>p.includes(m.k)?p.filter(x=>x!==m.k):[...p,m.k])}
            style={{padding:"5px 12px",borderRadius:20,border:`1.5px solid ${m.c}`,background:active.includes(m.k)?`${m.c}22`:"transparent",color:active.includes(m.k)?m.c:C.muted,fontSize:12,fontWeight:600,cursor:"pointer"}}>
            {m.l}
          </button>
        ))}
      </div>
      <div style={{background:C.card,border:`1px solid ${C.border}`,borderRadius:16,padding:"16px 4px"}}>
        <ResponsiveContainer width="100%" height={260}>
          <LineChart data={data} margin={{top:5,right:16,left:-10,bottom:5}}>
            <CartesianGrid strokeDasharray="3 3" stroke="rgba(255,255,255,0.05)"/>
            <XAxis dataKey="date" tick={{fill:C.muted,fontSize:10}} tickLine={false} axisLine={false}/>
            <YAxis tick={{fill:C.muted,fontSize:10}} tickLine={false} axisLine={false}/>
            <Tooltip contentStyle={{background:"#0a1a15",border:`1px solid ${C.accent}44`,borderRadius:10,fontSize:12}} labelStyle={{color:C.muted}}/>
            {metrics.filter(m=>active.includes(m.k)).map(m=>(
              <Line key={m.k} type="monotone" dataKey={m.k} name={m.l} stroke={m.c} strokeWidth={2.5} dot={{fill:m.c,r:3}} connectNulls={false}/>
            ))}
          </LineChart>
        </ResponsiveContainer>
      </div>
    </div>
  );
}

// ── NUTRITION ──
function NutritionPlan({athlete,plan,onUpdate,onAIGenerate,aiLoading}){
  const [week,setWeek]=useState(1);
  const weeks=plan?.weeks||[];
  const cw=weeks.find(w=>w.num===week)||{num:week,days:{}};

  function exportPDF(){
    const totalWeeks=plan?.totalWeeks||4;
    let html=`<html><head><meta charset="utf-8"><style>
      body{font-family:Arial,sans-serif;color:#111;padding:24px;max-width:800px;margin:0 auto;}
      h1{color:#00a07a;font-size:22px;margin-bottom:4px;}
      h2{color:#00a07a;font-size:16px;margin:20px 0 10px;border-bottom:2px solid #00a07a;padding-bottom:4px;}
      h3{font-size:13px;color:#333;margin:12px 0 6px;}
      .info{font-size:13px;color:#555;margin-bottom:16px;}
      .week{page-break-after:always;}
      .day{background:#f9fffe;border:1px solid #d0f0e8;border-radius:8px;padding:12px;margin-bottom:10px;}
      .day-title{font-weight:bold;color:#007a5e;font-size:14px;margin-bottom:8px;}
      .meals{display:grid;grid-template-columns:1fr 1fr;gap:8px;}
      .meal label{font-size:10px;color:#888;display:block;margin-bottom:2px;text-transform:uppercase;}
      .meal p{font-size:12px;margin:0;color:#222;min-height:18px;}
      @media print{body{padding:10px;}.week{page-break-after:always;}}
    </style></head><body>`;
    html+=`<h1>🥗 Plan de Alimentación</h1>`;
    html+=`<div class="info"><strong>${athlete.name}</strong> · ${athlete.sport} · ${athlete.age||"—"} años · ${athlete.height||"—"} cm · Objetivo: ${athlete.goal||"—"}<br>Coach: Enrique Monserrat · Pesoca10 · Generado: ${new Date().toLocaleDateString("es-AR")}</div>`;
    for(let w=1;w<=totalWeeks;w++){
      const wd=weeks.find(x=>x.num===w)||{num:w,days:{}};
      html+=`<div class="week"><h2>Semana ${w}</h2>`;
      DAYS.forEach(day=>{
        html+=`<div class="day"><div class="day-title">${day}</div><div class="meals">`;
        MEALS.forEach(meal=>{
          const val=wd.days?.[day]?.[meal]||"—";
          html+=`<div class="meal"><label>${meal}</label><p>${val}</p></div>`;
        });
        html+=`</div></div>`;
      });
      html+=`</div>`;
    }
    html+=`</body></html>`;
    const w2=window.open("","_blank");
    w2.document.write(html); w2.document.close();
    setTimeout(()=>w2.print(),400);
  }

  function setMeal(day,meal,val){
    const nw=[...weeks];const wi=nw.findIndex(w=>w.num===week);
    const wd=wi>=0?{...nw[wi]}:{num:week,days:{}};
    wd.days={...wd.days,[day]:{...wd.days[day],[meal]:val}};
    if(wi>=0) nw[wi]=wd; else nw.push(wd);
    onUpdate({...plan,weeks:nw,totalWeeks:plan?.totalWeeks||4});
  }
  return(
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14,flexWrap:"wrap",gap:8}}>
        <span style={{fontSize:13,color:C.muted}}>Plan <strong style={{color:C.text}}>{plan?.totalWeeks||4} semanas</strong></span>
        <div style={{display:"flex",gap:7}}>
          <Btn small onClick={exportPDF}>🖨️ Imprimir/PDF</Btn>
          <Btn primary small onClick={onAIGenerate} disabled={aiLoading}>{aiLoading?"⏳ Generando...":"🤖 IA genera plan"}</Btn>
        </div>
      </div>
      <div style={{display:"flex",gap:6,marginBottom:14,flexWrap:"wrap"}}>
        {Array.from({length:plan?.totalWeeks||4},(_,i)=>i+1).map(w=>(
          <button key={w} onClick={()=>setWeek(w)} style={{padding:"6px 14px",borderRadius:20,border:`1.5px solid ${w===week?C.accent:C.border}`,background:w===week?`${C.accent}22`:"transparent",color:w===week?C.accent:C.muted,fontSize:13,fontWeight:700,cursor:"pointer"}}>
            Sem {w}
          </button>
        ))}
      </div>
      {DAYS.map(day=>(
        <div key={day} style={{background:C.card,border:`1px solid ${C.border}`,borderRadius:14,padding:14,marginBottom:10}}>
          <div style={{fontWeight:700,color:C.accent,fontSize:13,marginBottom:10}}>{day}</div>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8}}>
            {MEALS.map(meal=>(
              <div key={meal}>
                <label style={{fontSize:11,color:C.muted,display:"block",marginBottom:3}}>{meal}</label>
                <textarea value={cw.days?.[day]?.[meal]||""} onChange={e=>setMeal(day,meal,e.target.value)}
                  placeholder="Ej: Avena + banana + leche" rows={2}
                  style={{width:"100%",background:"rgba(255,255,255,0.04)",border:`1px solid ${C.border}`,borderRadius:8,padding:"7px 10px",color:C.text,fontSize:12,outline:"none",resize:"none",boxSizing:"border-box",fontFamily:"inherit"}}/>
              </div>
            ))}
          </div>
        </div>
      ))}
    </div>
  );
}

// ── TRAINING ──
function TrainingPlan({athlete,plan,onUpdate,onAIGenerate,aiLoading}){
  const [week,setWeek]=useState(1);
  const weeks=plan?.weeks||[];
  const cw=weeks.find(w=>w.num===week)||{num:week,days:{}};

  function exportPDF(){
    const totalWeeks=plan?.totalWeeks||4;
    let html=`<html><head><meta charset="utf-8"><style>
      body{font-family:Arial,sans-serif;color:#111;padding:24px;max-width:800px;margin:0 auto;}
      h1{color:#7c3aed;font-size:22px;margin-bottom:4px;}
      h2{color:#7c3aed;font-size:16px;margin:20px 0 10px;border-bottom:2px solid #7c3aed;padding-bottom:4px;}
      .info{font-size:13px;color:#555;margin-bottom:16px;}
      .week{page-break-after:always;}
      .day{background:#faf9ff;border:1px solid #e0d8ff;border-radius:8px;padding:12px;margin-bottom:10px;}
      .day-title{font-weight:bold;color:#5b21b6;font-size:14px;margin-bottom:6px;}
      .day p{font-size:13px;margin:0;color:#222;white-space:pre-wrap;}
      @media print{body{padding:10px;}.week{page-break-after:always;}}
    </style></head><body>`;
    html+=`<h1>🏋️ Plan de Entrenamiento</h1>`;
    html+=`<div class="info"><strong>${athlete.name}</strong> · ${athlete.sport} · ${athlete.age||"—"} años · Objetivo: ${athlete.goal||"—"}<br>Coach: Enrique Monserrat · Pesoca10 · Generado: ${new Date().toLocaleDateString("es-AR")}</div>`;
    for(let w=1;w<=totalWeeks;w++){
      const wd=weeks.find(x=>x.num===w)||{num:w,days:{}};
      html+=`<div class="week"><h2>Semana ${w}</h2>`;
      DAYS.forEach(day=>{
        const val=wd.days?.[day]||"DESCANSO";
        html+=`<div class="day"><div class="day-title">${day}</div><p>${val}</p></div>`;
      });
      html+=`</div>`;
    }
    html+=`</body></html>`;
    const w2=window.open("","_blank");
    w2.document.write(html); w2.document.close();
    setTimeout(()=>w2.print(),400);
  }

  function setDay(day,val){
    const nw=[...weeks];const wi=nw.findIndex(w=>w.num===week);
    const wd=wi>=0?{...nw[wi]}:{num:week,days:{}};
    wd.days={...wd.days,[day]:val};
    if(wi>=0) nw[wi]=wd; else nw.push(wd);
    onUpdate({...plan,weeks:nw,totalWeeks:plan?.totalWeeks||4});
  }
  return(
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14,flexWrap:"wrap",gap:8}}>
        <span style={{fontSize:13,color:C.muted}}>Rutina <strong style={{color:C.text}}>{plan?.totalWeeks||4} semanas</strong></span>
        <div style={{display:"flex",gap:7}}>
          <Btn small onClick={exportPDF}>🖨️ Imprimir/PDF</Btn>
          <Btn primary small onClick={onAIGenerate} disabled={aiLoading}>{aiLoading?"⏳ Generando...":"🤖 IA genera rutina"}</Btn>
        </div>
      </div>
      <div style={{display:"flex",gap:6,marginBottom:14,flexWrap:"wrap"}}>
        {Array.from({length:plan?.totalWeeks||4},(_,i)=>i+1).map(w=>(
          <button key={w} onClick={()=>setWeek(w)} style={{padding:"6px 14px",borderRadius:20,border:`1.5px solid ${w===week?C.accent:C.border}`,background:w===week?`${C.accent}22`:"transparent",color:w===week?C.accent:C.muted,fontSize:13,fontWeight:700,cursor:"pointer"}}>
            Sem {w}
          </button>
        ))}
      </div>
      {DAYS.map(day=>(
        <div key={day} style={{background:C.card,border:`1px solid ${C.border}`,borderRadius:14,padding:14,marginBottom:10}}>
          <div style={{fontWeight:700,color:"#a78bfa",fontSize:13,marginBottom:8}}>{day}</div>
          <textarea value={cw.days?.[day]||""} onChange={e=>setDay(day,e.target.value)}
            placeholder={`Entrenamiento del ${day} — o DESCANSO`} rows={3}
            style={{width:"100%",background:"rgba(255,255,255,0.04)",border:`1px solid ${C.border}`,borderRadius:10,padding:"9px 12px",color:C.text,fontSize:13,outline:"none",resize:"vertical",boxSizing:"border-box",fontFamily:"inherit"}}/>
        </div>
      ))}
    </div>
  );
}

// ── REMINDERS ──
function Reminders({athlete,reminders,onAdd,onDelete}){
  const [show,setShow]=useState(false);
  const [form,setForm]=useState({date:"",type:"Control de medidas",note:""});
  const mine=reminders.filter(r=>r.athleteId===athlete.id).sort((a,b)=>new Date(a.date)-new Date(b.date));
  const upcoming=mine.filter(r=>r.date>=today());
  const past=mine.filter(r=>r.date<today());
  return(
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14}}>
        <span style={{fontSize:13,color:C.muted}}>{upcoming.length} próximo{upcoming.length!==1?"s":""}</span>
        <Btn primary onClick={()=>setShow(true)}>+ Recordatorio</Btn>
      </div>
      {mine.length===0&&<div style={{textAlign:"center",padding:"30px",color:C.muted}}><div style={{fontSize:36,marginBottom:8}}>🗓️</div><div>Agendá controles cada 15 días</div></div>}
      {upcoming.length>0&&<>
        <div style={{fontSize:11,fontWeight:700,color:C.accent,textTransform:"uppercase",letterSpacing:"1px",marginBottom:8}}>Próximos</div>
        {upcoming.map(r=>(
          <div key={r.id} style={{background:`${C.accent}0e`,border:`1px solid ${C.accent}33`,borderRadius:12,padding:"11px 14px",marginBottom:8,display:"flex",justifyContent:"space-between",alignItems:"center"}}>
            <div><div style={{fontWeight:700,color:C.text,fontSize:13}}>{r.type}</div><div style={{fontSize:12,color:C.muted,marginTop:2}}>📅 {fdate(r.date)}{r.note&&` · ${r.note}`}</div></div>
            <button onClick={()=>onDelete(r.id)} style={{background:"none",border:"none",color:C.muted,cursor:"pointer",fontSize:18}}>✕</button>
          </div>
        ))}
      </>}
      {past.length>0&&<>
        <div style={{fontSize:11,fontWeight:700,color:C.muted,textTransform:"uppercase",letterSpacing:"1px",margin:"14px 0 8px"}}>Pasados</div>
        {past.map(r=>(
          <div key={r.id} style={{background:C.card,border:`1px solid ${C.border}`,borderRadius:12,padding:"11px 14px",marginBottom:8,display:"flex",justifyContent:"space-between",alignItems:"center",opacity:0.45}}>
            <div><div style={{fontWeight:700,color:C.text,fontSize:13}}>{r.type}</div><div style={{fontSize:12,color:C.muted,marginTop:2}}>📅 {fdate(r.date)}{r.note&&` · ${r.note}`}</div></div>
            <button onClick={()=>onDelete(r.id)} style={{background:"none",border:"none",color:C.muted,cursor:"pointer",fontSize:18}}>✕</button>
          </div>
        ))}
      </>}
      {show&&(
        <Modal title="Nuevo recordatorio" onClose={()=>setShow(false)}>
          <Sel label="Tipo" value={form.type} onChange={v=>setForm(p=>({...p,type:v}))} options={["Control de medidas","Entrega de plan","Seguimiento nutricional","Competencia","Otro"]}/>
          <Input label="Fecha" value={form.date} onChange={v=>setForm(p=>({...p,date:v}))} type="date"/>
          <Input label="Nota opcional" value={form.note} onChange={v=>setForm(p=>({...p,note:v}))} placeholder="Ej: Antes del torneo"/>
          <div style={{display:"flex",gap:10,marginTop:8}}>
            <Btn onClick={()=>setShow(false)}>Cancelar</Btn>
            <button onClick={()=>{if(form.date){onAdd({id:uid(),athleteId:athlete.id,...form});setShow(false);}}}
              style={{flex:2,padding:"11px",borderRadius:10,border:"none",background:grad,color:"#fff",fontSize:14,fontWeight:700,cursor:"pointer"}}>Guardar ✓</button>
          </div>
        </Modal>
      )}
    </div>
  );
}

// ── CHAT ──
function Chat({athlete}){
  const [msgs,setMsgs]=useState(athlete._chat||[]);
  const [input,setInput]=useState("");
  const [loading,setLoading]=useState(false);
  const endRef=useRef(null);
  const txRef=useRef(null);
  useEffect(()=>{endRef.current?.scrollIntoView({behavior:"smooth"});},[msgs,loading]);
  const last=athlete.measurements?.length>0?[...athlete.measurements].sort((a,b)=>new Date(b.date)-new Date(a.date))[0]:null;
  const sys=`Eres un asistente experto en nutrición deportiva y entrenamiento. Ayudás al coach con este atleta:
PERFIL: ${athlete.name} | ${athlete.gender==="F"?"Femenino":"Masculino"} | ${athlete.sport} | ${athlete.age||"N/D"} años | ${athlete.height||"N/D"} cm
Objetivo: ${athlete.goal||"No definido"} | Restricciones: ${athlete.notes||"Ninguna"}
${last?`ÚLTIMA MEDICIÓN (${fdate(last.date)}): Peso ${last.weight||"N/D"}kg | %Grasa ${last.fatPercent||"N/D"}% | Masa magra ${last.leanMass||"N/D"}kg | IMC ${last.imc||"N/D"} | Cintura ${last.waist||"N/D"}cm | Total mediciones: ${athlete.measurements.length}`:"Sin mediciones."}
Respondé de forma profesional, específica y práctica. Para planes de alimentación o entrenamiento, sé muy detallado.`;

  async function send(){
    if(!input.trim()||loading) return;
    const um={role:"user",content:input.trim()};
    const nm=[...msgs,um]; setMsgs(nm); setInput(""); setLoading(true);
    try{
      const r=await fetch("https://api.anthropic.com/v1/messages",{method:"POST",headers:{"Content-Type":"application/json"},body:JSON.stringify({model:"claude-sonnet-4-20250514",max_tokens:1000,system:sys,messages:nm.map(m=>({role:m.role,content:m.content}))})});
      const d=await r.json();
      const reply=d.content?.map(b=>b.text||"").join("")||"Sin respuesta.";
      const upd=[...nm,{role:"assistant",content:reply}];
      setMsgs(upd); athlete._chat=upd;
    }catch{
      const upd=[...nm,{role:"assistant",content:"Error de conexión."}];
      setMsgs(upd); athlete._chat=upd;
    }
    setLoading(false);
  }
  const QUICK=["Crea un plan nutricional de 4 semanas","Diseña una rutina de entrenamiento","Analiza su composición corporal","¿Qué suplementos le recomendarías?"];
  return(
    <div style={{display:"flex",flexDirection:"column",height:"100%",minHeight:0}}>
      <div style={{flex:1,overflowY:"auto",paddingBottom:8}}>
        {msgs.length===0?(
          <div style={{display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",minHeight:200,textAlign:"center",padding:"20px 10px"}}>
            <div style={{fontSize:36,marginBottom:8}}>{ICONS[athlete.sport]||"🏅"}</div>
            <div style={{fontSize:15,fontWeight:700,color:C.text,marginBottom:4}}>Chat con {athlete.name}</div>
            <div style={{fontSize:12,color:C.muted,marginBottom:16}}>La IA conoce su perfil y mediciones</div>
            <div style={{display:"flex",flexWrap:"wrap",gap:7,justifyContent:"center"}}>
              {QUICK.map(q=><button key={q} onClick={()=>{setInput(q);setTimeout(()=>txRef.current?.focus(),50);}} style={{padding:"7px 13px",borderRadius:20,background:`${C.accent}10`,border:`1px solid ${C.accent}33`,color:C.accent,fontSize:12,cursor:"pointer"}}>{q}</button>)}
            </div>
          </div>
        ):(
          <>
            {msgs.map((m,i)=>(
              <div key={i} style={{display:"flex",justifyContent:m.role==="user"?"flex-end":"flex-start",marginBottom:10}}>
                {m.role==="assistant"&&<div style={{width:26,height:26,borderRadius:"50%",background:grad,display:"flex",alignItems:"center",justifyContent:"center",fontSize:13,marginRight:7,flexShrink:0,alignSelf:"flex-end"}}>🤖</div>}
                <div style={{maxWidth:"80%",background:m.role==="user"?grad:"rgba(255,255,255,0.06)",color:"#fff",borderRadius:m.role==="user"?"18px 18px 4px 18px":"18px 18px 18px 4px",padding:"10px 14px",fontSize:13.5,lineHeight:1.6,whiteSpace:"pre-wrap",wordBreak:"break-word",border:m.role==="user"?"none":`1px solid ${C.border}`}}>{m.content}</div>
              </div>
            ))}
            {loading&&<div style={{display:"flex",alignItems:"center",gap:8,marginBottom:10}}><div style={{width:26,height:26,borderRadius:"50%",background:grad,display:"flex",alignItems:"center",justifyContent:"center",fontSize:13}}>🤖</div><div style={{background:"rgba(255,255,255,0.06)",borderRadius:"18px 18px 18px 4px",padding:"10px 14px",border:`1px solid ${C.border}`}}><span style={{display:"flex",gap:4}}>{[0,1,2].map(i=><span key={i} style={{width:6,height:6,background:C.accent,borderRadius:"50%",display:"inline-block",animation:"pulse 1.2s ease-in-out infinite",animationDelay:`${i*0.2}s`}}/>)}</span></div></div>}
            <div ref={endRef}/>
          </>
        )}
      </div>
      <div style={{paddingTop:10,flexShrink:0}}>
        <div style={{display:"flex",gap:8,alignItems:"flex-end"}}>
          <textarea ref={txRef} value={input} onChange={e=>setInput(e.target.value)} onKeyDown={e=>{if(e.key==="Enter"&&!e.shiftKey){e.preventDefault();send();}}} placeholder={`Preguntá sobre ${athlete.name}...`} rows={2}
            style={{flex:1,background:"rgba(255,255,255,0.05)",border:`1.5px solid ${C.accent}44`,borderRadius:12,padding:"10px 13px",color:C.text,fontSize:13.5,outline:"none",resize:"none",fontFamily:"inherit",lineHeight:1.5,maxHeight:100,overflowY:"auto"}}/>
          <button onClick={send} disabled={!input.trim()||loading} style={{width:44,height:44,borderRadius:11,border:"none",background:input.trim()&&!loading?grad:"rgba(255,255,255,0.06)",color:input.trim()&&!loading?"#fff":C.muted,fontSize:18,cursor:input.trim()&&!loading?"pointer":"default",display:"flex",alignItems:"center",justifyContent:"center",flexShrink:0}}>↑</button>
        </div>
      </div>
    </div>
  );
}

// ── MAIN ──
export default function CoachPro(){
  const [data,setData]=useState({athletes:[],reminders:[]});
  const [selId,setSelId]=useState(null);
  const [tab,setTab]=useState("meas");
  const [sidebar,setSidebar]=useState(true);
  const [modal,setModal]=useState(null);
  const [editTarget,setEditTarget]=useState(null);
  const [aiLoading,setAiLoading]=useState(false);
  const [saveStatus,setSaveStatus]=useState("idle");
  const [loaded,setLoaded]=useState(false);
  const [showArchive,setShowArchive]=useState(false);
  const importRef=useRef(null);

  // ── LOAD from persistent storage on mount ──
  useEffect(()=>{
    async function loadData(){
      try{
        // Try Claude persistent storage first
        if(typeof window.storage !== "undefined"){
          const result = await window.storage.get("coachpro_main");
          if(result && result.value){
            const parsed = JSON.parse(result.value);
            if(parsed.athletes) parsed.athletes = parsed.athletes.map(a=>({...a,archived:a.archived||false}));
            setData(parsed);
            const active = parsed.athletes?.filter(a=>!a.archived);
            if(active?.length>0) setSelId(active[0].id);
            setLoaded(true); return;
          }
        }
      }catch(e){}
      // Fallback: localStorage
      try{
        const s = localStorage.getItem("pesoca10_data");
        if(s){
          const parsed = JSON.parse(s);
          if(parsed.athletes) parsed.athletes = parsed.athletes.map(a=>({...a,archived:a.archived||false}));
          setData(parsed);
          const active = parsed.athletes?.filter(a=>!a.archived);
          if(active?.length>0) setSelId(active[0].id);
        }
      }catch(e){}
      setLoaded(true);
    }
    loadData();
  },[]);

  // ── SAVE: tries Claude storage, always saves to localStorage too ──
  const saveTimer = useRef(null);
  useEffect(()=>{
    if(!loaded) return;
    clearTimeout(saveTimer.current);
    setSaveStatus("saving");
    saveTimer.current = setTimeout(async()=>{
      const json = JSON.stringify(data);
      let ok = false;
      // Try Claude persistent storage
      try{
        if(typeof window.storage !== "undefined"){
          await window.storage.set("coachpro_main", json);
          ok = true;
        }
      }catch(e){}
      // Always also save to localStorage as backup
      try{ localStorage.setItem("pesoca10_data", json); ok = true; }catch(e){}
      setSaveStatus(ok ? "saved" : "error");
      if(ok) setTimeout(()=>setSaveStatus("idle"),2000);
    }, 800);
  },[data, loaded]);

  const athlete=data.athletes.find(a=>a.id===selId);

  function mut(id,fn){ setData(p=>({...p,athletes:p.athletes.map(a=>a.id===id?fn(a):a)})); }

  function addAthlete(f){
    const a={id:uid(),...f,name:f.name.trim(),measurements:[],nutritionPlan:{totalWeeks:4,weeks:[]},trainingPlan:{totalWeeks:4,weeks:[]},_chat:[]};
    setData(p=>({...p,athletes:[a,...p.athletes]}));
    setSelId(a.id); setTab("meas"); setModal(null);
  }
  function delAthlete(id){ if(!confirm("¿Eliminar definitivamente? Esta acción no se puede deshacer.")) return; setData(p=>({...p,athletes:p.athletes.filter(a=>a.id!==id)})); if(selId===id) setSelId(null); }
  function archiveAthlete(id){ mut(id,a=>({...a,archived:true,archivedAt:today()})); if(selId===id) setSelId(null); }
  function restoreAthlete(id){ mut(id,a=>({...a,archived:false,archivedAt:null})); setSelId(id); setShowArchive(false); setTab("meas"); }
  function saveMeas(m){
    mut(selId,a=>{const ex=a.measurements.find(x=>x.id===m.id);return{...a,measurements:ex?a.measurements.map(x=>x.id===m.id?m:x):[...a.measurements,m]};});
    setModal(null); setEditTarget(null);
  }
  function delMeas(id){ mut(selId,a=>({...a,measurements:a.measurements.filter(m=>m.id!==id)})); }
  function updateNutrition(plan){ mut(selId,a=>({...a,nutritionPlan:plan})); }
  function updateTraining(plan){ mut(selId,a=>({...a,trainingPlan:plan})); }
  function addReminder(r){ setData(p=>({...p,reminders:[...p.reminders,r]})); }
  function delReminder(id){ setData(p=>({...p,reminders:p.reminders.filter(r=>r.id!==id)})); }

  // ── EXPORT ──
  function exportData(){
    const blob=new Blob([JSON.stringify(data,null,2)],{type:"application/json"});
    const url=URL.createObjectURL(blob);
    const a=document.createElement("a"); a.href=url;
    a.download=`coachpro_backup_${today()}.json`; a.click();
    URL.revokeObjectURL(url);
  }
  // ── IMPORT ──
  function importData(e){
    const file=e.target.files?.[0]; if(!file) return;
    const reader=new FileReader();
    reader.onload=ev=>{
      try{
        const parsed=JSON.parse(ev.target.result);
        if(parsed.athletes){
          setData(parsed);
          if(parsed.athletes.length>0) setSelId(parsed.athletes[0].id);
          alert("✅ Datos importados correctamente");
        }
      }catch{ alert("❌ Archivo inválido"); }
    };
    reader.readAsText(file);
    e.target.value="";
  }

  async function aiGeneratePlan(type){
    if(!athlete||aiLoading) return;
    setAiLoading(true);
    const last=athlete.measurements?.length>0?[...athlete.measurements].sort((a,b)=>new Date(b.date)-new Date(a.date))[0]:null;
    const prompt=type==="nutrition"
      ?`Crea un plan de alimentación de 4 semanas para:\nNombre: ${athlete.name} | Deporte: ${athlete.sport} | ${athlete.gender==="F"?"Femenino":"Masculino"} | ${athlete.age||"N/D"} años | ${athlete.height||"N/D"} cm | Peso: ${last?.weight||"N/D"} kg | Objetivo: ${athlete.goal||"N/D"} | Restricciones: ${athlete.notes||"Ninguna"}\n\nDevuelve SOLO JSON sin markdown:\n{"totalWeeks":4,"weeks":[{"num":1,"days":{"Lunes":{"Desayuno":"...","Media mañana":"...","Almuerzo":"...","Merienda":"...","Cena":"...","Post-entreno":"..."},"Martes":{...},"Miércoles":{...},"Jueves":{...},"Viernes":{...},"Sábado":{...},"Domingo":{...}}},...]}`
      :`Crea una rutina de entrenamiento de 4 semanas para:\nNombre: ${athlete.name} | Deporte: ${athlete.sport} | ${athlete.gender==="F"?"Femenino":"Masculino"} | ${athlete.age||"N/D"} años | Objetivo: ${athlete.goal||"N/D"} | Restricciones: ${athlete.notes||"Ninguna"}\n\nDevuelve SOLO JSON sin markdown:\n{"totalWeeks":4,"weeks":[{"num":1,"days":{"Lunes":"detalle del entrenamiento o DESCANSO","Martes":"...","Miércoles":"...","Jueves":"...","Viernes":"...","Sábado":"...","Domingo":"DESCANSO"}},{"num":2,...},{"num":3,...},{"num":4,...}]}`;
    try{
      const r=await fetch("https://api.anthropic.com/v1/messages",{method:"POST",headers:{"Content-Type":"application/json"},body:JSON.stringify({model:"claude-sonnet-4-20250514",max_tokens:1000,messages:[{role:"user",content:prompt}]})});
      const d=await r.json();
      const txt=d.content?.map(b=>b.text||"").join("")||"";
      const plan=JSON.parse(txt.replace(/```json|```/g,"").trim());
      if(type==="nutrition") updateNutrition(plan); else updateTraining(plan);
    }catch{ alert("Error al generar. Intenta de nuevo."); }
    setAiLoading(false);
  }

  const upcomingCount=data.reminders.filter(r=>selId&&r.athleteId===selId&&r.date>=today()).length;

  if(!loaded) return(
    <div style={{height:"100vh",background:C.bg,display:"flex",alignItems:"center",justifyContent:"center",flexDirection:"column",gap:12}}>
      <img src="data:image/png;base64,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" style={{width:56,height:36,borderRadius:6,objectFit:"contain",background:"#f5c800",padding:"2px"}}/>
      <div style={{color:C.text,fontSize:18,fontWeight:800}}>Pesoca10</div>
      <div style={{color:C.muted,fontSize:13}}>Cargando datos...</div>
    </div>
  );

  return(
    <div style={{height:"100vh",display:"flex",background:C.bg,fontFamily:"'DM Sans','Segoe UI',sans-serif",overflow:"hidden",fontSize:14}}>

      {/* SIDEBAR */}
      {sidebar&&(
        <div style={{width:230,minWidth:230,background:C.sidebar,borderRight:`1px solid ${C.border}`,display:"flex",flexDirection:"column",overflow:"hidden"}}>
          <div style={{padding:"14px 12px 10px",borderBottom:`1px solid ${C.border}`}}>
            <div style={{display:"flex",alignItems:"center",gap:9,marginBottom:12}}>
              <img src="data:image/png;base64,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" style={{width:80,height:50,borderRadius:10,objectFit:"contain",background:"#f5c800",padding:"3px"}}/>
              <div><div style={{fontWeight:800,fontSize:14,color:C.text}}>Pesoca10</div><div style={{fontSize:10,color:C.muted}}>Enrique Monserrat</div></div>
            </div>
            <Btn primary full onClick={()=>setModal("newAthlete")}>+ Nuevo atleta</Btn>
          </div>
          <div style={{flex:1,overflowY:"auto",padding:"8px"}}>
            {/* ACTIVE ATHLETES */}
            {(()=>{
              const active=data.athletes.filter(a=>!a.archived);
              const archived=data.athletes.filter(a=>a.archived);
              return(<>
                {active.length===0?(
                  <div style={{textAlign:"center",padding:"24px 10px",color:C.muted,fontSize:12}}><div style={{fontSize:28,marginBottom:8}}>🏅</div>Creá tu primer atleta</div>
                ):active.map(a=>(
                  <div key={a.id} onClick={()=>{setSelId(a.id);setTab("meas");setShowArchive(false);}}
                    style={{background:a.id===selId?grad:"rgba(255,255,255,0.03)",border:`1px solid ${a.id===selId?"transparent":C.border}`,borderRadius:10,padding:"9px 10px",cursor:"pointer",marginBottom:6,display:"flex",alignItems:"center",gap:8,transition:"all 0.15s"}}>
                    <div style={{width:32,height:32,borderRadius:"50%",background:a.id===selId?"rgba(255,255,255,0.2)":`${C.accent}18`,display:"flex",alignItems:"center",justifyContent:"center",fontSize:15,flexShrink:0}}>{ICONS[a.sport]||"🏅"}</div>
                    <div style={{flex:1,minWidth:0}}>
                      <div style={{fontWeight:700,fontSize:13,color:a.id===selId?"#fff":C.text,overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{a.name}</div>
                      <div style={{fontSize:10,color:a.id===selId?"rgba(255,255,255,0.6)":C.muted,marginTop:1}}>{a.sport} · {a.measurements?.length||0} med.</div>
                    </div>
                    <button onClick={e=>{e.stopPropagation();if(confirm(`¿Archivar a ${a.name}? Sus datos se conservan.`)) archiveAthlete(a.id);}}
                      title="Archivar atleta"
                      style={{background:"none",border:"none",cursor:"pointer",color:a.id===selId?"rgba(255,255,255,0.4)":"rgba(255,255,255,0.15)",fontSize:13,padding:2,flexShrink:0}}>📦</button>
                  </div>
                ))}

                {/* ARCHIVE TOGGLE */}
                {archived.length>0&&(
                  <>
                    <button onClick={()=>setShowArchive(o=>!o)}
                      style={{width:"100%",padding:"7px 10px",borderRadius:10,border:`1px solid ${C.border}`,background:"transparent",color:C.muted,fontSize:11,fontWeight:700,cursor:"pointer",display:"flex",alignItems:"center",justifyContent:"space-between",marginTop:6}}>
                      <span>📦 Archivo ({archived.length})</span>
                      <span>{showArchive?"▲":"▼"}</span>
                    </button>
                    {showArchive&&archived.map(a=>(
                      <div key={a.id} style={{background:"rgba(255,255,255,0.02)",border:`1px solid ${C.border}`,borderRadius:10,padding:"9px 10px",marginTop:5,display:"flex",alignItems:"center",gap:8,opacity:0.7}}>
                        <div style={{width:30,height:30,borderRadius:"50%",background:"rgba(255,255,255,0.06)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:14,flexShrink:0}}>{ICONS[a.sport]||"🏅"}</div>
                        <div style={{flex:1,minWidth:0}}>
                          <div style={{fontWeight:700,fontSize:12,color:C.muted,overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{a.name}</div>
                          <div style={{fontSize:10,color:"#2a5a4a",marginTop:1}}>Archivado {a.archivedAt?fdate(a.archivedAt):""}</div>
                        </div>
                        <div style={{display:"flex",flexDirection:"column",gap:3}}>
                          <button onClick={()=>restoreAthlete(a.id)} title="Restaurar"
                            style={{background:`${C.accent}18`,border:`1px solid ${C.accent}44`,borderRadius:6,color:C.accent,fontSize:10,padding:"3px 7px",cursor:"pointer",fontWeight:700}}>↩ Restaurar</button>
                          <button onClick={()=>delAthlete(a.id)} title="Eliminar definitivamente"
                            style={{background:"rgba(255,107,107,0.08)",border:"1px solid rgba(255,107,107,0.2)",borderRadius:6,color:C.danger,fontSize:10,padding:"3px 7px",cursor:"pointer",fontWeight:700}}>🗑️ Borrar</button>
                        </div>
                      </div>
                    ))}
                  </>
                )}
              </>);
            })()}
          </div>
          {/* Bottom: save status + backup buttons */}
          <div style={{padding:"8px 12px 12px",borderTop:`1px solid ${C.border}`}}>
            <div style={{display:"flex",alignItems:"center",gap:6,marginBottom:8}}>
              <div style={{width:6,height:6,borderRadius:"50%",background:saveStatus==="saved"?C.accent:saveStatus==="saving"?C.warn:saveStatus==="error"?C.danger:"#333",flexShrink:0}}/>
              <span style={{fontSize:10,color:C.muted}}>{saveStatus==="saved"?"Guardado ✓":saveStatus==="saving"?"Guardando...":saveStatus==="error"?"Error al guardar":"Listo"}</span>
            </div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:6}}>
              <button onClick={exportData} style={{padding:"6px 0",borderRadius:8,border:`1px solid ${C.border}`,background:"transparent",color:C.muted,fontSize:11,cursor:"pointer",fontWeight:600}}>⬇️ Exportar</button>
              <button onClick={()=>importRef.current?.click()} style={{padding:"6px 0",borderRadius:8,border:`1px solid ${C.border}`,background:"transparent",color:C.muted,fontSize:11,cursor:"pointer",fontWeight:600}}>⬆️ Importar</button>
            </div>
            <input ref={importRef} type="file" accept=".json" onChange={importData} style={{display:"none"}}/>
          </div>
        </div>
      )}

      {/* MAIN */}
      <div style={{flex:1,display:"flex",flexDirection:"column",overflow:"hidden",minWidth:0}}>
        {/* TOPBAR */}
        <div style={{padding:"10px 13px",borderBottom:`1px solid ${C.border}`,display:"flex",alignItems:"center",gap:10,background:"rgba(0,0,0,0.2)",flexShrink:0}}>
          <button onClick={()=>setSidebar(o=>!o)} style={{background:"rgba(255,255,255,0.06)",border:"none",borderRadius:8,color:C.muted,width:30,height:30,cursor:"pointer",fontSize:14,flexShrink:0}}>☰</button>
          {athlete?(
            <>
              <div style={{width:34,height:34,borderRadius:"50%",background:grad,display:"flex",alignItems:"center",justifyContent:"center",fontSize:17,flexShrink:0}}>{ICONS[athlete.sport]||"🏅"}</div>
              <div style={{flex:1,minWidth:0}}>
                <div style={{fontWeight:800,color:C.text,fontSize:14,overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{athlete.name}</div>
                <div style={{fontSize:10,color:C.muted}}>{athlete.sport}{athlete.age?` · ${athlete.age}a`:""}{athlete.height?` · ${athlete.height}cm`:""}{athlete.gender?` · ${athlete.gender==="F"?"♀":"♂"}`:""}</div>
              </div>
              <button onClick={()=>{setEditTarget(athlete);setModal("editAthlete");}} style={{background:"rgba(255,255,255,0.06)",border:"none",borderRadius:8,color:C.muted,padding:"5px 10px",cursor:"pointer",fontSize:12,flexShrink:0}}>✏️</button>
              {!athlete.archived&&<button onClick={()=>{if(confirm(`¿Archivar a ${athlete.name}?`)) archiveAthlete(athlete.id);}} title="Archivar" style={{background:"rgba(255,255,255,0.06)",border:"none",borderRadius:8,color:C.muted,padding:"5px 10px",cursor:"pointer",fontSize:12,flexShrink:0}}>📦</button>}
            </>
          ):(
            <div style={{color:C.muted,fontSize:13}}>Seleccioná un atleta</div>
          )}
        </div>

        {/* TABS */}
        {athlete&&(
          <div style={{display:"flex",borderBottom:`1px solid ${C.border}`,flexShrink:0,background:"rgba(0,0,0,0.12)",overflowX:"auto"}}>
            {TABS.map(t=>(
              <button key={t.id} onClick={()=>setTab(t.id)}
                style={{padding:"10px 12px",border:"none",background:"transparent",color:t.id===tab?C.accent:C.muted,fontSize:13,fontWeight:700,cursor:"pointer",borderBottom:`2px solid ${t.id===tab?C.accent:"transparent"}`,transition:"all 0.15s",whiteSpace:"nowrap",flexShrink:0,position:"relative"}}>
                {t.l}
                {t.id==="reminders"&&upcomingCount>0&&<span style={{background:C.warn,color:"#000",borderRadius:"50%",width:14,height:14,fontSize:9,fontWeight:800,display:"inline-flex",alignItems:"center",justifyContent:"center",position:"absolute",top:5,right:2}}>{upcomingCount}</span>}
              </button>
            ))}
          </div>
        )}

        {/* CONTENT */}
        <div style={{flex:1,overflowY:"auto",padding:athlete?15:0,display:"flex",flexDirection:"column"}}>
          {!athlete?(
            <div style={{flex:1,display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",color:C.muted,textAlign:"center",padding:24}}>
              <img src="data:image/png;base64,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" style={{width:130,height:82,borderRadius:12,objectFit:"contain",background:"#f5c800",padding:"4px",marginBottom:12}}/>
              <div style={{fontSize:19,fontWeight:800,color:"#7ab8a8",marginBottom:8}}>Pesoca10</div>
              <div style={{fontSize:12,color:C.muted,marginBottom:4}}>Enrique Monserrat</div>
              <div style={{fontSize:13,maxWidth:260,lineHeight:1.7,marginBottom:20}}>Tus datos se guardan automáticamente. Seleccioná un atleta o creá uno nuevo.</div>
              <Btn primary onClick={()=>setModal("newAthlete")}>+ Crear primer atleta</Btn>
            </div>
          ):tab==="meas"?<MeasList athlete={athlete} measurements={athlete.measurements||[]} onNew={()=>setModal("newMeas")} onEdit={m=>{setEditTarget(m);setModal("editMeas");}} onDelete={delMeas}/>
          :tab==="charts"?<Charts measurements={athlete.measurements||[]}/>
          :tab==="nutrition"?<NutritionPlan athlete={athlete} plan={athlete.nutritionPlan||{totalWeeks:4,weeks:[]}} onUpdate={updateNutrition} onAIGenerate={()=>aiGeneratePlan("nutrition")} aiLoading={aiLoading}/>
          :tab==="training"?<TrainingPlan athlete={athlete} plan={athlete.trainingPlan||{totalWeeks:4,weeks:[]}} onUpdate={updateTraining} onAIGenerate={()=>aiGeneratePlan("training")} aiLoading={aiLoading}/>
          :tab==="reminders"?<Reminders athlete={athlete} reminders={data.reminders} onAdd={addReminder} onDelete={delReminder}/>
          :tab==="chat"?<Chat athlete={athlete} key={athlete.id}/>
          :null}
        </div>
      </div>

      {modal==="newAthlete"&&<AthleteForm onSave={addAthlete} onClose={()=>setModal(null)}/>}
      {modal==="editAthlete"&&editTarget&&<AthleteForm existing={editTarget} onSave={f=>{mut(editTarget.id,a=>({...a,...f,name:f.name.trim()}));setModal(null);setEditTarget(null);}} onClose={()=>{setModal(null);setEditTarget(null);}}/>}
      {modal==="newMeas"&&athlete&&<MeasForm athlete={athlete} onSave={saveMeas} onClose={()=>setModal(null)}/>}
      {modal==="editMeas"&&editTarget&&athlete&&<MeasForm athlete={athlete} existing={editTarget} onSave={saveMeas} onClose={()=>{setModal(null);setEditTarget(null);}}/>}

      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;600;700;800&display=swap');
        *{box-sizing:border-box;}
        ::-webkit-scrollbar{width:3px;height:3px;}
        ::-webkit-scrollbar-thumb{background:rgba(0,212,168,0.2);border-radius:4px;}
        input[type=date]::-webkit-calendar-picker-indicator{filter:invert(0.5);}
        @keyframes pulse{0%,80%,100%{opacity:.2;transform:scale(.8)}40%{opacity:1;transform:scale(1)}}
      `}</style>
    </div>
  );
}
