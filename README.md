#Halloween
use_bpm 90
live_loop :biitti do
  sample :bd_808, rate: 1, amp: 4
  sleep 1
  sample :elec_hi_snare, amp: 1
  sleep 1
  sample :bd_808, rate: 1, amp: 4
  sleep 1
  sample :elec_hi_snare, amp: 1
  sleep 1
end
use_bpm 90
live_loop :kitaramelodia do
  sample_free :guit_e_fifths, rate: 0.5, amp: 1.5
  sample :guit_e_fifths, rate: 1, amp: 0.8
  sleep 1.5
  sample :guit_e_fifths, rate: 1.5, amp: 0.8
  sleep 1.5
  sample :guit_e_fifths, rate: 1.4, amp: 0.8
  sleep 3
  sample :guit_e_slide, rate: 1, amp: 0.8
  sleep 2
end
live_loop :hihat do
  8 .times do
    sample :drum_cymbal_hard, start: 0.25, finish: 0.5, rate: 3, amp: 0.5 + rrand(-0.1, 0.1)
    sleep 0.125
  end
  4.times do
    sample :bd_ada, start: 0.05, finish: 0.6, rate: 3, amp: 0.5 + rrand(-0.1, 0.1)
    sleep 0.25
  end
  16.times do
    sample :drum_snare_soft, start: 0.5, finish: 0.5, rate: 2, amp: 1 + rrand(-0.1, 0.1)
    sleep 0.5
  end
  use_bpm 40
  sample :elec_pop
  use_synth_defaults amp: 0.5, attack: 0.5, release:0.025
  with_fx :tremolo do
    play [:C4, :E4, :G4, :A4].ring.tick, pan: rrand(1, 0.95)
    sleep 1
  end
  live_loop :echo do
    play 50
    sleep 0.5
    sample :elec_plip
    sleep 0.75
    play 60
    live_loop :bpf do
      use_synth :pretty_bell
      play 50
      sleep 0.5
      play 60
    end
    with_fx :echo do
      play 60
      with_fx :reverb do
        play 50
        sleep 0.5
        play 50
      end
     end 
    end
  end
end
