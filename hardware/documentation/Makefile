all: reDIP-RIOT-sch.pdf reDIP-RIOT-pcb.pdf reDIP-RIOT-BOM.xlsx

reDIP-RIOT-sch.pdf: ../reDIP-RIOT.kicad_sch
	kicad-cli sch export pdf $< -o $@
reDIP-RIOT-pcb.pdf: ../reDIP-RIOT.kicad_pcb
	kicad-cli pcb export pdf $< --layers "F.Cu,In1.Cu,In2.Cu,B.Cu,B.Paste,F.Paste,B.SilkS,F.SilkS,B.Mask,F.Mask,Dwgs.User,Edge.Cuts,B.CrtYd,F.CrtYd,B.Fab,F.Fab" -o $@
reDIP-RIOT-BOM.xlsx: reDIP-RIOT-bom.xml
	kicost -i $< --fields Notes --overwrite -o $@
reDIP-RIOT-bom.xml: ../reDIP-RIOT.kicad_sch
	kicad-cli sch export python-bom $<

.PHONY: all
