SELECT  BMS_SA_SETTLE_DTLQRY_V.SASETTLEID,  DECODE(BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN8, NULL,         BMS_SA_SETTLE_DTLQRY_V.CREDATE, BMS_SA_SETTLE_DTLQRY_V.CONFIRMDATE)                                                                                            CREDATE,  BMS_SA_SETTLE_DTLQRY_V.SA_MODE,  BMS_SA_SETTLE_DTLQRY_V.CUSTOMID,  BMS_SA_SETTLE_DTLQRY_V.INVTYPE,  BMS_SA_SETTLE_DTLQRY_V.CUSTOMOPCODE,  BMS_SA_SETTLE_DTLQRY_V.CUSTOMNAME,  (SELECT sum(nvl(t.zxcolumn5 * t.goodsqty,                  t.total_line))   FROM bms_sa_settle_dtl t   WHERE t.sasettleid =         BMS_SA_SETTLE_DTLQRY_V.SASETTLEID)                                                 TOTAL,  BMS_SA_SETTLE_DTLQRY_V.INPUTMANID,  BMS_SA_SETTLE_DTLQRY_V.INPUTMANNAME,  BMS_SA_SETTLE_DTLQRY_V.DTL_LINES,  BMS_SA_SETTLE_DTLQRY_V.MEMO,  BMS_SA_SETTLE_DTLQRY_V.SETTLEGROUPNO,  BMS_SA_SETTLE_DTLQRY_V.SETTLETYPEID,  BMS_SA_SETTLE_DTLQRY_V.GATHERINGATONCE,  BMS_SA_SETTLE_DTLQRY_V.CERTID,  BMS_SA_SETTLE_DTLQRY_V.CERTNO,  BMS_SA_SETTLE_DTLQRY_V.CERTUSESTATUS,  BMS_SA_SETTLE_DTLQRY_V.USESTATUS,  BMS_SA_SETTLE_DTLQRY_V.INITFLAG,  BMS_SA_SETTLE_DTLQRY_V.SASETTLEDTLID,  BMS_SA_SETTLE_DTLQRY_V.INVLISTID,  BMS_SA_SETTLE_DTLQRY_V.INVLISTFIRSTNO,  BMS_SA_SETTLE_DTLQRY_V.INVLISTNO,  BMS_SA_SETTLE_DTLQRY_V.PRINTNO,  BMS_SA_SETTLE_DTLQRY_V.PRINTLINE,  BMS_SA_SETTLE_DTLQRY_V.GOODSID,  BMS_SA_SETTLE_DTLQRY_V.OPCODE,  BMS_SA_SETTLE_DTLQRY_V.GOODSNO,  BMS_SA_SETTLE_DTLQRY_V.GOODSNAME,  BMS_SA_SETTLE_DTLQRY_V.GOODSTYPE,  BMS_SA_SETTLE_DTLQRY_V.PRODAREA,  BMS_SA_SETTLE_DTLQRY_V.GOODSUNIT,  BMS_SA_SETTLE_DTLQRY_V.GOODSQTY,  ceil(abs(BMS_SA_SETTLE_DTLQRY_V.GOODSQTY) / (SELECT packsize                                               FROM                                                 BMS_SA_DOCTOSET A, BMS_SA_DTL B, PUB_GOODS_DETAIL C                                               WHERE a.sadtlid =                                                     b.salesdtlid AND b.goodsdtlid = c.goodsdtlid AND                                                     a.sasettledtlid =                                                     BMS_SA_SETTLE_DTLQRY_V.SASETTLEDTLID)) packsizenum,  BMS_SA_SETTLE_DTLQRY_V.GOODSQTY1,  BMS_SA_SETTLE_DTLQRY_V.GOODSUNIT1,  BMS_SA_SETTLE_DTLQRY_V.UNITPRICE,  BMS_SA_SETTLE_DTLQRY_V.TOTAL_LINE,  BMS_SA_SETTLE_DTLQRY_V.TAXRATE,  BMS_SA_SETTLE_DTLQRY_V.TAXMONEY,  BMS_SA_SETTLE_DTLQRY_V.NOTAXMONEY,  BMS_SA_SETTLE_DTLQRY_V.SALERID,  BMS_SA_SETTLE_DTLQRY_V.SALERNAME,  BMS_SA_SETTLE_DTLQRY_V.SALESDEPTID,  BMS_SA_SETTLE_DTLQRY_V.SALESDEPTNAME,  BMS_SA_SETTLE_DTLQRY_V.SKFLAG,  BMS_SA_SETTLE_DTLQRY_V.COSTINGMONEY,  BMS_SA_SETTLE_DTLQRY_V.COSTALTER,  BMS_SA_SETTLE_DTLQRY_V.PRESENTCOST,  BMS_SA_SETTLE_DTLQRY_V.DTLMEMO,  BMS_SA_SETTLE_DTLQRY_V.PROXYFLAG,  BMS_SA_SETTLE_DTLQRY_V.RECFINFLAG,  BMS_SA_SETTLE_DTLQRY_V.SHOULESETTLEMONEY,  BMS_SA_SETTLE_DTLQRY_V.INVID,  BMS_SA_SETTLE_DTLQRY_V.INVFIRSTNO,  BMS_SA_SETTLE_DTLQRY_V.INVNO,  BMS_SA_SETTLE_DTLQRY_V.INVTYPE_A,  BMS_SA_SETTLE_DTLQRY_V.INVDTLID,  BMS_SA_SETTLE_DTLQRY_V.TOTALRECQTY,  BMS_SA_SETTLE_DTLQRY_V.TOTALRECMONEY,  BMS_SA_SETTLE_DTLQRY_V.OTHERSETTLEFLAG,  BMS_SA_SETTLE_DTLQRY_V.SADISCOUNTMONEY,  BMS_SA_SETTLE_DTLQRY_V.CORRECTFLAG,  BMS_SA_SETTLE_DTLQRY_V.CORRECTCPLID,  BMS_SA_SETTLE_DTLQRY_V.SKCERTID,  BMS_SA_SETTLE_DTLQRY_V.SKCERTNO,  BMS_SA_SETTLE_DTLQRY_V.SKCERTUSESTATUS,  BMS_SA_SETTLE_DTLQRY_V.RECINGQTY,  BMS_SA_SETTLE_DTLQRY_V.RECINGMONEY,  BMS_SA_SETTLE_DTLQRY_V.ENTRYID,  BMS_SA_SETTLE_DTLQRY_V.ENTRYNAME,  BMS_SA_SETTLE_DTLQRY_V.CUSTOMNO,  BMS_SA_SETTLE_DTLQRY_V.SKCERTCREDATE,  BMS_SA_SETTLE_DTLQRY_V.CERTCREDATE,  BMS_SA_SETTLE_DTLQRY_V.ENGLISHSHORT,  BMS_SA_SETTLE_DTLQRY_V.FMID,  BMS_SA_SETTLE_DTLQRY_V.FMNAME,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN1,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN2,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN3,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN4,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN52                                                      DTLZXCOLUMN52,  to_number(BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN5)                                            DTLZXCOLUMN5,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN6,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN7,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN8,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN9,  BMS_SA_SETTLE_DTLQRY_V.DTLZXCOLUMN10,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN1,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN2,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN3,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN4,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN5,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN6,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN7,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN8,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN9,  BMS_SA_SETTLE_DTLQRY_V.DOCZXCOLUMN10,  BMS_SA_SETTLE_DTLQRY_V.CONFIRMDATE,  BMS_SA_SETTLE_DTLQRY_V.CONFIRMMANID,  BMS_SA_SETTLE_DTLQRY_V.CONFIRMMANNAME,  BMS_SA_SETTLE_DTLQRY_V.FPRQ,  BMS_SA_SETTLE_DTLQRY_V.YSKTS,  BMS_SA_SETTLE_DTLQRY_V.CQTS,  BMS_SA_SETTLE_DTLQRY_V.EARLIESTLACKDAYS,  BMS_SA_SETTLE_DTLQRY_V.NOID15,  BMS_SA_SETTLE_DTLQRY_V.NONAME15,  BMS_SA_SETTLE_DTLQRY_V.NO13,  bms_sa_settle_dtlqry_v.exchange,  pf_sasettranflag1(sasettledtlid)                                                          DELIVERMETHOD,  pf_sasetTARGETPOSADDR1(sasettledtlid)                                                     TARGETPOSADDR,  protocolid,  ratime,  BMS_SA_SETTLE_DTLQRY_V.LXDATE,  BMS_SA_SETTLE_DTLQRY_V.CNONAME17,  BMS_SA_SETTLE_DTLQRY_V.CNOID17,  PF_GET_PLATFORMID(BMS_SA_SETTLE_DTLQRY_V.GOODSID)                                         platformid,  BMS_SA_SETTLE_DTLQRY_V.realcustomname,  BMS_SA_SETTLE_DTLQRY_V.NBPZH,  BMS_SA_SETTLE_DTLQRY_V.NO07,  BMS_SA_SETTLE_DTLQRY_V.DZSETTLEID,  BMS_SA_SETTLE_DTLQRY_V.DZINVNOFROM BMS_SA_SETTLE_DTLQRY_VWHERE 1 = 1;

sasettleid	结算总单ID	bms_sa_settle_dtlqry_v.sasettleid	null	no
credate	结算日期	credate	null	no
sa_mode	销售模式	bms_sa_settle_dtlqry_v.sa_mode	null	no
customid	客户标识号	bms_sa_settle_dtlqry_v.customid	null	no
invtype	合同类型	bms_sa_settle_dtlqry_v.invtype	null	no
customopcode	客户操作码	bms_sa_settle_dtlqry_v.customopcode	null	no
customname	客户名称	bms_sa_settle_dtlqry_v.customname	null	no
total	结算总单金额	total	null	no
inputmanid	录入员标识号	bms_sa_settle_dtlqry_v.inputmanid	null	no
inputmanname	录入人	bms_sa_settle_dtlqry_v.inputmanname	null	no
dtl_lines	细目笔数	bms_sa_settle_dtlqry_v.dtl_lines	null	no
memo	备注	bms_sa_settle_dtlqry_v.memo	null	no
settlegroupno	结算组号	bms_sa_settle_dtlqry_v.settlegroupno	null	no
settletypeid	结算方式	bms_sa_settle_dtlqry_v.settletypeid	null	no
gatheringatonce	现收金额	bms_sa_settle_dtlqry_v.gatheringatonce	null	no
certid	传票ID	bms_sa_settle_dtlqry_v.certid	null	no
certno	传票号	bms_sa_settle_dtlqry_v.certno	null	no
certusestatus	传票状态	bms_sa_settle_dtlqry_v.certusestatus	null	no
usestatus	使用状态	bms_sa_settle_dtlqry_v.usestatus	null	no
initflag	初始标志	bms_sa_settle_dtlqry_v.initflag	null	no
sasettledtlid	结算细单ID	bms_sa_settle_dtlqry_v.sasettledtlid	null	no
invlistid	发票清单ID	bms_sa_settle_dtlqry_v.invlistid	null	no
invlistfirstno	清单轨号	bms_sa_settle_dtlqry_v.invlistfirstno	null	no
invlistno	清单号	bms_sa_settle_dtlqry_v.invlistno	null	no
printno	打印号	bms_sa_settle_dtlqry_v.printno	null	no
printline	打印行号	bms_sa_settle_dtlqry_v.printline	null	no
goodsid	货品标识号	bms_sa_settle_dtlqry_v.goodsid	null	no
opcode	货品操作码	bms_sa_settle_dtlqry_v.opcode	null	no
goodsno	货品分类码	bms_sa_settle_dtlqry_v.goodsno	null	no
goodsname	货品名称	bms_sa_settle_dtlqry_v.goodsname	null	no
goodstype	货品规格	bms_sa_settle_dtlqry_v.goodstype	null	no
prodarea	产地	bms_sa_settle_dtlqry_v.prodarea	null	no
goodsunit	基本单位	bms_sa_settle_dtlqry_v.goodsunit	null	no
goodsqty	结算数量	bms_sa_settle_dtlqry_v.goodsqty	null	no
packsizenum	件数	packsizenum	null	no
goodsqty1	计价单位数量	bms_sa_settle_dtlqry_v.goodsqty1	null	no
goodsunit1	计价单位	bms_sa_settle_dtlqry_v.goodsunit1	null	no
unitprice	unitprice_t	bms_sa_settle_dtlqry_v.unitprice	null	no
total_line	total_line_t	bms_sa_settle_dtlqry_v.total_line	null	no
taxrate	税率	bms_sa_settle_dtlqry_v.taxrate	null	no
taxmoney	税额	bms_sa_settle_dtlqry_v.taxmoney	null	no
notaxmoney	价额	bms_sa_settle_dtlqry_v.notaxmoney	null	no
salerid	业务员标识号	bms_sa_settle_dtlqry_v.salerid	null	no
salername	业务员姓名	bms_sa_settle_dtlqry_v.salername	null	no
salesdeptid	销售部门标识号	bms_sa_settle_dtlqry_v.salesdeptid	null	no
salesdeptname	业务部门	bms_sa_settle_dtlqry_v.salesdeptname	null	no
skflag	记存货帐标志	bms_sa_settle_dtlqry_v.skflag	null	no
costingmoney	销售成本	bms_sa_settle_dtlqry_v.costingmoney	null	no
costalter	摊成本调整金额	bms_sa_settle_dtlqry_v.costalter	null	no
presentcost	摊赠样成本	bms_sa_settle_dtlqry_v.presentcost	null	no
dtlmemo	细目备注	bms_sa_settle_dtlqry_v.dtlmemo	null	no
proxyflag	托收标志	bms_sa_settle_dtlqry_v.proxyflag	null	no
recfinflag	收款完成标志	bms_sa_settle_dtlqry_v.recfinflag	null	no
shoulesettlemoney	应结金额	bms_sa_settle_dtlqry_v.shoulesettlemoney	null	no
invid	发票标识号	bms_sa_settle_dtlqry_v.invid	null	no
invfirstno	发票轨号	bms_sa_settle_dtlqry_v.invfirstno	null	no
invno	发票号	bms_sa_settle_dtlqry_v.invno	null	no
invtype_a	发票类型	bms_sa_settle_dtlqry_v.invtype_a	null	no
invdtlid	发票明细标识号	bms_sa_settle_dtlqry_v.invdtlid	null	no
totalrecqty	累计收款数量	bms_sa_settle_dtlqry_v.totalrecqty	null	no
totalrecmoney	累计收款金额	bms_sa_settle_dtlqry_v.totalrecmoney	null	no
othersettleflag	其它应收标志	bms_sa_settle_dtlqry_v.othersettleflag	null	no
sadiscountmoney	销售折扣金额	bms_sa_settle_dtlqry_v.sadiscountmoney	null	no
correctflag	冲调标志	bms_sa_settle_dtlqry_v.correctflag	null	no
correctcplid	冲调单据标识号	bms_sa_settle_dtlqry_v.correctcplid	null	no
skcertid	存货传票标识号	bms_sa_settle_dtlqry_v.skcertid	null	no
skcertno	存货传票号	bms_sa_settle_dtlqry_v.skcertno	null	no
skcertusestatus	存货传票状态	bms_sa_settle_dtlqry_v.skcertusestatus	null	no
recingqty	期票未收款数量	bms_sa_settle_dtlqry_v.recingqty	null	no
recingmoney	期票未收款金额	bms_sa_settle_dtlqry_v.recingmoney	null	no
entryid	独立核算单元号	bms_sa_settle_dtlqry_v.entryid	null	no
entryname	独立核算单元	bms_sa_settle_dtlqry_v.entryname	null	no
customno	客户编码	bms_sa_settle_dtlqry_v.customno	null	no
skcertcredate	存货传票日期	bms_sa_settle_dtlqry_v.skcertcredate	null	no
certcredate	传票日期	bms_sa_settle_dtlqry_v.certcredate	null	no
englishshort	币种缩写	bms_sa_settle_dtlqry_v.englishshort	null	no
fmid	币种ID	bms_sa_settle_dtlqry_v.fmid	null	no
fmname	币种名称	bms_sa_settle_dtlqry_v.fmname	null	no
dtlzxcolumn1	Dtlzxcolumn1_t	bms_sa_settle_dtlqry_v.dtlzxcolumn1	null	no
dtlzxcolumn2	Dtlzxcolumn2_t	bms_sa_settle_dtlqry_v.dtlzxcolumn2	null	no
dtlzxcolumn3	行号	bms_sa_settle_dtlqry_v.dtlzxcolumn3	null	no
dtlzxcolumn4	Dtlzxcolumn4_t	bms_sa_settle_dtlqry_v.dtlzxcolumn4	null	no
dtlzxcolumn52	票面价	bms_sa_settle_dtlqry_v.dtlzxcolumn52	null	no
dtlzxcolumn5	Dtlzxcolumn5_t	dtlzxcolumn5	null	no
dtlzxcolumn6	Dtlzxcolumn6_t	bms_sa_settle_dtlqry_v.dtlzxcolumn6	null	no
dtlzxcolumn7	Dtlzxcolumn7_t	bms_sa_settle_dtlqry_v.dtlzxcolumn7	null	no
dtlzxcolumn8	Dtlzxcolumn8_t	bms_sa_settle_dtlqry_v.dtlzxcolumn8	null	no
dtlzxcolumn9	Dtlzxcolumn9_9	bms_sa_settle_dtlqry_v.dtlzxcolumn9	null	no
dtlzxcolumn10	Dtlzxcolumn10_t	bms_sa_settle_dtlqry_v.dtlzxcolumn10	null	no
doczxcolumn1	行号	bms_sa_settle_dtlqry_v.doczxcolumn1	null	no
doczxcolumn2	行号	bms_sa_settle_dtlqry_v.doczxcolumn2	null	no
doczxcolumn3	Doczxcolumn3_t	bms_sa_settle_dtlqry_v.doczxcolumn3	null	no
doczxcolumn4	Doczxcolumn4_t	bms_sa_settle_dtlqry_v.doczxcolumn4	null	no
doczxcolumn5	Doczxcolumn5_t	bms_sa_settle_dtlqry_v.doczxcolumn5	null	no
doczxcolumn6	Doczxcolumn6_t	bms_sa_settle_dtlqry_v.doczxcolumn6	null	no
doczxcolumn7	Doczxcolumn7_t	bms_sa_settle_dtlqry_v.doczxcolumn7	null	no
doczxcolumn8	Doczxcolumn8_t	bms_sa_settle_dtlqry_v.doczxcolumn8	null	no
doczxcolumn9	Doczxcolumn9_t	bms_sa_settle_dtlqry_v.doczxcolumn9	null	no
doczxcolumn10	Doczxcolumn10_t	bms_sa_settle_dtlqry_v.doczxcolumn10	null	no
confirmdate	确定时间	bms_sa_settle_dtlqry_v.confirmdate	null	no
confirmmanid	确定人ID	bms_sa_settle_dtlqry_v.confirmmanid	null	no
confirmmanname	确定人姓名	bms_sa_settle_dtlqry_v.confirmmanname	null	no
fprq	fprq_t	bms_sa_settle_dtlqry_v.fprq	null	no
yskts	收款天数期限	bms_sa_settle_dtlqry_v.yskts	null	no
cqts	超期天数	bms_sa_settle_dtlqry_v.cqts	null	no
earliestlackdays	默认最早欠款天数	bms_sa_settle_dtlqry_v.earliestlackdays	null	no
noid15	厂牌ID	bms_sa_settle_dtlqry_v.noid15	null	no
noname15	厂牌	bms_sa_settle_dtlqry_v.noname15	null	no
no13	功效属性一级	bms_sa_settle_dtlqry_v.no13	null	no
exchange	汇率	bms_sa_settle_dtlqry_v.exchange	null	no
delivermethod	送货方式	delivermethod	null	no
targetposaddr	送货地址	targetposaddr	null	no
protocolid	折扣协议ID	bms_sa_settle_dtlqry_v.protocolid	null	no
ratime	传票记帐日期	bms_sa_settle_dtlqry_v.ratime	null	no
lxdate	流向日期	bms_sa_settle_dtlqry_v.lxdate	null	no
cnoname17	规划分类	bms_sa_settle_dtlqry_v.cnoname17	null	no
cnoid17	cnoid17_t	bms_sa_settle_dtlqry_v.cnoid17	null	no
platformid	货品平台ID	platformid	null	no
realcustomname	实际客户名称	bms_sa_settle_dtlqry_v.realcustomname	null	no
nbpzh	内部凭证号	bms_sa_settle_dtlqry_v.nbpzh	null	no
no07	处方属性一级	bms_sa_settle_dtlqry_v.no07	null	no
dzsettleid	大众结算单ID	bms_sa_settle_dtlqry_v.dzsettleid	null	no
dzinvno	大众发票号	bms_sa_settle_dtlqry_v.dzinvno	null	no

-- 下面关键表的注释

CREATE TABLE BMS_SA_SETTLE_DOC
(
    SASETTLEID NUMBER(10) PRIMARY KEY NOT NULL,
    CREDATE DATE,
    SA_MODE NUMBER(1),
    CUSTOMID NUMBER(10),
    CUSTOMNAME VARCHAR2(60),
    TOTAL NUMBER(12,2),
    INPUTMANID NUMBER(10),
    DTL_LINES NUMBER(5),
    MEMO VARCHAR2(200),
    SETTLEGROUPNO VARCHAR2(10),
    SETTLETYPEID NUMBER(3),
    GATHERINGATONCE NUMBER(12,2),
    CERTID NUMBER(10),
    USESTATUS NUMBER(1),
    INVTYPE NUMBER(2),
    INITFLAG NUMBER(1),
    ENTRYID NUMBER(10),
    TOTALREC NUMBER(12,2),
    FMID NUMBER(10),
    EXCHANGE NUMBER(20,12),
    ZXCOLUMN1 VARCHAR2(50),
    ZXCOLUMN2 VARCHAR2(50),
    ZXCOLUMN3 VARCHAR2(50),
    ZXCOLUMN4 VARCHAR2(50),
    ZXCOLUMN5 VARCHAR2(50),
    ZXCOLUMN6 VARCHAR2(50),
    ZXCOLUMN7 VARCHAR2(50),
    ZXCOLUMN8 VARCHAR2(50),
    ZXCOLUMN9 VARCHAR2(50),
    ZXCOLUMN10 VARCHAR2(50),
    CONFIRMDATE DATE,
    CONFIRMMANID NUMBER(10),
    ZXCOLUMN11 VARCHAR2(50),
    ZXCOLUMN12 VARCHAR2(50),
    ZXCOLUMN13 VARCHAR2(50),
    ZXCOLUMN14 VARCHAR2(50),
    ZXCOLUMN15 VARCHAR2(50),
    ZXCOLUMN16 VARCHAR2(50),
    ZXCOLUMN17 VARCHAR2(50),
    ZXCOLUMN18 VARCHAR2(50),
    ZXCOLUMN19 VARCHAR2(50),
    ZXCOLUMN20 VARCHAR2(50),
    CONSTRAINT BMS_SASET_CUSTOMID_FK FOREIGN KEY (CUSTOMID) REFERENCES PUB_CUSTOMER (CUSTOMID),
    CONSTRAINT BMS_SASET_DOC_ENTRYID FOREIGN KEY (ENTRYID) REFERENCES PUB_ENTRY (ENTRYID)
);
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.SASETTLEID IS '销售结算单标识号';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CREDATE IS '日期';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.SA_MODE IS '"1-	普通销售2-	先配后结3-	发出销售4-	委托销售"';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CUSTOMID IS '客户标识号';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CUSTOMNAME IS '客户名称';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.TOTAL IS '总金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.INPUTMANID IS '录入员标识号';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.DTL_LINES IS '细目笔数';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.MEMO IS '备注';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.SETTLEGROUPNO IS '结算组号';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.SETTLETYPEID IS '结算方式 详见PUB_SETTLETYPE_DDL字典表';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.GATHERINGATONCE IS '大众商场现收金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CERTID IS '传票标识号';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.USESTATUS IS '"使用状态0-	作废1-	临时2-	确定"';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.INVTYPE IS '1-增值税发票 2-普通发票';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.INITFLAG IS '初始标志';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ENTRYID IS '核算单元ID';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.TOTALREC IS '累计收款金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.FMID IS '外币ID';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.EXCHANGE IS '汇率';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN1 IS '专项字段';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN2 IS '大众商场开票标志';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN3 IS '专项字段';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN4 IS '记录大众商场开票结算时医保刷卡金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN5 IS '记录大众商场开票结算时银联卡刷卡金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN6 IS '记录大众商场开票结算时现金金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN7 IS '记录大众商场开票结算时医保品种总金额';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN8 IS '专项字段';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN9 IS '清单打印标志';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.ZXCOLUMN10 IS '已打印时间序列号(年月日时)';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CONFIRMDATE IS '确定时间';
COMMENT ON COLUMN BMS_SA_SETTLE_DOC.CONFIRMMANID IS '确定人ID';
CREATE INDEX BMS_SASETDOC_CREDATE_IDX ON BMS_SA_SETTLE_DOC (CREDATE);
CREATE INDEX BMS_SASET_CUSTOMID_IDX ON BMS_SA_SETTLE_DOC (CUSTOMID);
CREATE INDEX SA_SET_DOC_CERTID_IDX ON BMS_SA_SETTLE_DOC (CERTID);
